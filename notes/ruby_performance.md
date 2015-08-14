##Code to measure

    def factorial(i)
        return i if i < 2
        return factorial(i-1) + factorial(i-2)
    end

###Benchmark

    require 'benchmark'

    Benchmark.realtime { factorial(1000) }

    Benchmark.bmbm do |bm|
      bm.report{ factor(1000)}
    end

###Benchmark.ips

    #gem 'benchmark-ips'
    require 'benchmark/ips'

    benchmark.ips do |bm|
        bm.report('factorial') { factorial(1000) }
    end

##Memory and GC

###GC

    GC.stat
    =>
    {
                            :count => 12,
                        :heap_used => 145,
                      :heap_length => 145,
                   :heap_increment => 0,
                   :heap_live_slot => 57604,
                   :heap_free_slot => 1492,
                  :heap_final_slot => 0,
                  :heap_swept_slot => 25820,
            :heap_eden_page_length => 142,
            :heap_tomb_page_length => 3,
           :total_allocated_object => 197236,
               :total_freed_object => 139632,
                  :malloc_increase => 251584,
                     :malloc_limit => 16777216,
                   :minor_gc_count => 9,
                   :major_gc_count => 3,
          :remembered_shady_object => 452,
    :remembered_shady_object_limit => 428,
                       :old_object => 23467,
                 :old_object_limit => 37056,
               :oldmalloc_increase => 2449568,
                  :oldmalloc_limit => 16777216
    }

    GC::Profiler.disable

###memory_profiler

    #gem memory_profiler
    require 'memory_profiler'


##CPU Profiling

###ruby_prof

    #gem ruby-prof
    require 'ruby-prof'


##3 guidelines for Rails profile
- Always profile on production
- Disable GC
- Profile at least twice and ignore the 1st result
