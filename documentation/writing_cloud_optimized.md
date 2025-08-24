# Tips for Writing Cloud-optimized Code

## 1. Leverage Cloud Storage Efficiently

**Avoid downloading large datasets:** Instead of downloading large datasets to your local machine, access them directly from cloud storage (e.g., Amazon S3, Google Cloud Storage).
Use libraries like `s3fs` or `gcsfs` to interact with cloud storage as if it were a local file system.

**Use cloud-native data formats:** Cloud environments often work better with optimized data formats such as **Parquet** or **HDF5**.
These formats allow for faster reading and writing of data, especially when working with large datasets.

## 2. Distribute Computations

**Parallelize tasks:** When dealing with large-scale data or complex computations, use distributed computing frameworks like **Dask** or **Ray**.
These tools allow you to scale computations across multiple machines, leveraging the full power of cloud resources.

**Split and process data in chunks:** If your data is too large to fit in memory, split it into smaller chunks and process each chunk in parallel.
This is especially important when working with large catalogs or time-series data.

**Example:** The [forced photometry notebook](https://nasa-fornax.github.io/fornax-demo-notebooks/forced_photometry/multiband_photometry.html) demonstrates an analysis workflow that operates on a large dataset but can be efficiently parallelized.
It gathers a substantial number of astronomical images and applies the same photometric extraction procedure to each one.
Since each image can be processed independently, the workload is distributed across multiple worker processes, each executing the same code on a different subset of images.
This parallel approach significantly reduces total processing time and is well-suited to cloud environments where compute resources can be scaled as needed.

**Example:** The [light curve collector notebook](https://nasa-fornax.github.io/fornax-demo-notebooks/light_curves/light_curve_collector.html) illustrates an analysis in which operations are time-consuming but can be executed independently across a dataset.
The workflow begins by selecting a sample of astronomical objects and then makes multiple independent queries—such as retrieving light curves from various archives—for each object.
Because these queries do not depend on one another, the workload can be parallelized by assigning different tasks (e.g., different archive queries) to separate worker processes.
Each worker operates on the same object sample but runs a distinct part of the pipeline, enabling faster execution through concurrent processing.

**Example** Our [scale up notebook](https://nasa-fornax.github.io/fornax-demo-notebooks/light_curves/scale_up.html) is a tutorial on parallelization of generating multiwavelength light curves with tools, tips, and suggestions relevant to many tasks.

## 3. Optimize Memory Usage

**Avoid loading entire datasets into memory:** Use libraries like **Dask**, **Vaex**, or **Zarr** that allow for out-of-core computations (processing data that doesn't fit in memory).

**Use lazy loading:** Libraries like **lsdb** and **HDF5** allow you to load and process data lazily, meaning data is read in chunks only when needed.

## 4. Minimize Data Movement

**Avoid moving data between cloud and local systems:** Whenever possible, keep the data within the cloud environment to avoid slow network transfers.
This is particularly important when working with large datasets.

## 5. Ensure Efficient Use of Cloud Resources

**Monitor cloud usage:** Cloud resources can accumulate costs quickly.
Make sure to monitor usage, scale down resources when not in use, and avoid long-term storage of unused data.

## 6. Optimize Code for CPU Usage (CPU Profiling)

**CPU profiling** is the process of measuring how much time your code spends running each part of your program, so you can find and fix performance bottlenecks.
In Python, this means tracking which functions are slow or use a lot of CPU so you can make your code run faster—especially useful when working with large datasets or running analyses in the cloud.

### CPU Profiling Methods in Jupyter Notebooks

-   **[%prun magic command](https://ipython.readthedocs.io/en/stable/interactive/magics.html#magic-prun)** – Quick function-level profiling.
-   **[cProfile module](https://docs.python.org/3/library/profile.html)** – Built-in Python profiler for detailed performance stats.
-   **[line_profiler with `%lprun`](https://github.com/pyutils/line_profiler)** – Line-by-line timing; requires installation.
-   **[\@profile decorator](https://github.com/pyutils/line_profiler#usage)** – Used with `line_profiler` for marking functions.
-   **[SnakeViz](https://jiffyclub.github.io/snakeviz/)** – Visualizes profiling output interactively.
-   **[Py-Spy](https://github.com/benfred/py-spy)** – Low-overhead sampling profiler (typically used outside notebooks).
-   **[Scalene](https://github.com/plasma-umass/scalene)** – Advanced profiler with CPU, memory, and line-level stats.
-   **[JupyterLab Profiler extensions](https://github.com/jupyterlab-contrib/jupyterlab-profiling)** – Optional profiling tools for enhanced visualization in notebooks.

## 7. Optimize for Memory Usage (Memory Profiling)

Memory profiling is a technique that helps track and understand how much memory your code uses during execution.
By identifying memory bottlenecks, you can optimize your code to handle larger datasets or reduce cloud resource costs.

### Memory Profiling Methods for Jupyter Notebooks

1.  **[memory_profiler](https://pypi.org/project/memory-profiler/)** – Tracks memory usage line-by-line in notebooks.
2.  **[objgraph](https://mg.pov.lt/objgraph/)** – Visualizes memory usage and helps identify memory leaks in notebooks.
3.  **[tracemalloc](https://docs.python.org/3/library/tracemalloc.html)** – Built-in Python library to trace memory allocation over time in notebooks.
4.  **[psutil](https://psutil.readthedocs.io/en/latest/)** – Provides information on system and process memory usage, works interactively in notebooks.
5.  **[guppy3](https://pypi.org/project/guppy3/)** – A Python memory profiler with heap analysis, usable in notebooks.
6.  **[pympler](https://pympler.readthedocs.io/en/latest/)** – Advanced memory profiling tool that tracks memory usage of Python objects, works in notebooks.
7.  **[dask](https://docs.dask.org/en/stable/)** – For handling large datasets in parallel and optimizing memory usage in distributed analyses in notebooks.
