include ../Makefile.include

all: orchestra-rb-ns orchestra-rb-storing orchestra-sb-storing orchestra-link-based lf 6tisch-min

orchestra-rb-ns: orchestra-rb-ns.json
	rm -rf results
	../../tsch-sim.sh $< > /dev/null
	grep "initializing rule unicast per neighbor non-storing" results/log.txt > /dev/null
	$(NODE) --harmony --experimental-modules  ../check_pdr.mjs results/stats.json 90.0

orchestra-rb-storing: orchestra-rb-storing.json
	rm -rf results
	../../tsch-sim.sh $< > /dev/null
	grep "initializing rule unicast per neighbor storing" results/log.txt > /dev/null
	grep "storing rule, receiver based" results/log.txt > /dev/null
	$(NODE) --harmony --experimental-modules  ../check_pdr.mjs results/stats.json 90.0

orchestra-sb-storing: orchestra-sb-storing.json
	rm -rf results
	../../tsch-sim.sh $< > /dev/null
	grep "initializing rule unicast per neighbor storing" results/log.txt > /dev/null
	grep "storing rule, sender based" results/log.txt > /dev/null
	$(NODE) --harmony --experimental-modules  ../check_pdr.mjs results/stats.json 95.0

orchestra-link-based: orchestra-link-based.json
	rm -rf results
	../../tsch-sim.sh $< > /dev/null
	grep "initializing rule unicast per neighbor link based" results/log.txt > /dev/null
	$(NODE) --harmony --experimental-modules  ../check_pdr.mjs results/stats.json 95.0

6tisch-min: 6tisch-min.json
	rm -rf results
	../../tsch-sim.sh $< > /dev/null
	grep "initializing 6tisch minimal" results/log.txt > /dev/null
	$(NODE) --harmony --experimental-modules  ../check_pdr.mjs results/stats.json 95.0

lf: lf.json
	rm -rf results
	../../tsch-sim.sh $< > /dev/null
	grep "initializing leaf-and-forwarder scheduler" results/log.txt > /dev/null
	$(NODE) --harmony --experimental-modules  ../check_pdr.mjs results/stats.json 95.0

clean:
	rm -rf results
