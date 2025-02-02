## Memory Management Configuration

One can explicitly specify the allowed amount of memory when running a native image.
`-Xmn` - to set the size of the young generation (the amount of memory that can be allocated without triggering a GC). The value is specified in bytes, suffix `k`, `m`, or `g` can be used for scaling, e.g., `-Xmn16M`, default `256M`.
`-Xmx` - maximum heap size in bytes. Note that this is not the maximum amount of consumed memory, because during GC the system can request more temporary memory, for example `-Xmx16M`, default unlimited.
`-Xms` - minimum heap size in bytes. The value is specified in bytes, suffix `k`, `m`, or `g` can be used for scaling. Heap space that is unused will be retained for future heap usage, rather than being returned to the operating system.

In addition, it is possible to fine-tune maximum memory to be used by an image. Set the percent value of physical
memory using the `-R:MaximumHeapSizePercent=<value>` option. For more
information, unfold the `native-image --expert-options-all` list and search for
`-R:MaximumHeapSizePercent=<value>`,
`-R:MaximumYoungGenerationSizePercent=<value>`,
`-H:AllocationBeforePhysicalMemorySize=<value>` and other related options.

As of version 20.1.0 option `-XX:MaxDirectMemorySize=...` was added to allow
controlling the maximum size of direct buffer allocations.

## Low Latency Garbage Collection

When using GraalVM Enterprise you can enable the experimental option to use a
lower latency garbage collection implementation. A lower latency GC should
improve the performance of the native image applications by reducing the
stop-the-world pauses.

To enable it use the `-H:+UseLowLatencyGC` option when building a native image.

Currently the lower latency GC works on Linux in the AMD64 builds. One can
configure the default runtime heap size at image build time, e.g.,
`-R:MinHeapSize=256m -R:MaxHeapSize=2g -R:MaxNewSize=128m`.

You can use `-XX:+PrintGC`, `-XX:+VerboseGC` to get some information about garbage collections.
