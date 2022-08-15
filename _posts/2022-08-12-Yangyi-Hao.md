---
layout: post
title: "Packages and Unit Tests in Python"
author: Yangyi Hao
---

## Package Interface
Wrapping our code into Python packages is a convenient way to modularize and publish our works. Currently, we are packing them in to `mcsim.monte_carlo` as individual functions. This way of packaging serves its functionalities but also come with some pitfalls. As it is right now, the user can only interact with the function `run_simulation` and it becomes fairly limited how the user can use the rest of the functions. Ideally, the user should be able to call individual functions and make their own simulations. On top of that, if the user does decide to call each individual functions, it would be convenient if they don't have to pass in all the function arguments at the same time.

Ideally, we can init our module in the following structure.

```
class MonteCarlo:

    def __init__(reduced_temperature, num_steps, max_displacement, cutoff, freq, file_path):
        reduced_temperature_ = reduced_temperature
        num_steps_ = num_steps
        max_displacement_ = max_displacement
        cutoff_ = cutoff
        freq_ = freq
        coordinates_, box_length_ = read_xyz(file_path)
        coordinates_np_ = np.array(coordinates)
        
    def calculate_tail_correction():
        num_particles = length(coordinates_)
        """
        Calculate the long range tail correction
        """
    
        const1 = (8 * math.pi * num_particles ** 2) / (3 * box_length_ ** 3)
        const2 = (1/3) * (1 / cutoff_)**9 - (1 / cutoff_) **3
    
        return const1 * const2
        
```

As can be seen above, take `caculate_tail_correction()` as an example, the user no longer has to pass in any arguments in to the function, and it would be much more convenient if the user does prefer to call this function as a standalong for whatever reasons.

This is good follow up that we can work on in the future.


## Adding NumPy

Indeed after today's (Thursday) revision, most of the numpy optimization seemed futile, and in fact performance drop was noticed in the final simulation. As shown in this[href="https://github.com/msse-2022-bootcamp/group-project-scott-s-tots/blob/main/Monte_Carlo_sims_NP.ipynb"] notebook.

---
w/o NumPy: 0.19s
w Numpy: 0.88s

---

We believed that it was because the final simulation was not incorporating the corresponding numpy optimization made to the helper functions. Simply converting the input coordinates into a numpy array doesn't do much, and in fact, because the helper functions were still expecting list inputs and outputing in python list as well, there were usually two layers of conversion between np arrays and list in and out of a function, which explained the deterioration of the performance.

After the weekend's work on packaging and incorprating np optimizations done on the helper functions. We had the following result.

---
w/o NumPy: 260s
w Numpy: 15s

---

The results were truly amazing. The numpy version of the final simulation was 17x faster.
