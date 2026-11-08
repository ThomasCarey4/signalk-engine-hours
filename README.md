# signalk-engine-hours-seren

Fork of [KEGustafsson/signalk-engine-hours](https://github.com/KEGustafsson/signalk-engine-hours) published as `signalk-engine-hours-seren`.

**What's different:** the original counts an engine as running whenever `revolutions > 0`. A stopped engine's rev sensor can report small phantom values (0.03–4 rev/s were seen at anchor), and every one of those added time to `runTime`. On one boat that inflated four months of engine hours by 45–70%. This fork adds a **`runningThreshold`** setting (rev/s, default **13.33** = 800 rpm). Revolutions at or below it count as stopped. Set it to `0` for the original behaviour.

The plugin id is still `signalk-engine-hours`, so an existing `engines.json`, plugin configuration and web app carry over. **Uninstall the original package before installing this one.** Both packages register the same plugin id.

Signal K engine hours logger keeps engine runtime data in persistent storage. Engines that report revolutions to the Signal K server are logged automatically. Users can change how often engine revolutions are monitored; the current default is 60s. When the Signal K server starts, previously logged data is read from persistent storage. Runtime data is written to persistent storage shortly after changes (debounced). From the WebApp, engine runtimes can be set and changed.

## Versions

- v0.0.1 Initial release
- v0.1.0 Improvements, custom API and simple hours editor
- v0.1.1 Improvements to editor
- v0.2.0 runTimeTrip added and improvements to editor
- v0.2.1 fix for runTimeTrip meta
- v0.3.0 editor UI modifications
- v0.3.1 fixes to editor UI
- v0.4.0 tooltip to show hrs:min
- v1.0.0 1st release
- v1.1.0 fix: improve error handling and validation for engine data
- v1.2.0 feat: option to monitor propulsion.*.state
- v1.3.0 new UI and fixes to code
- v1.3.1 chore: clean-up
- v1.4.0 feat: improved time calculation accuracy
- v1.4.1 fix: engine hours accrual bug
- v1.5.0 feat: engine hours reporing optimized 
- v1.6.0 fix: accrual clamp, auth, input hardening, UI state
- v1.7.0 (seren fork) feat: runningThreshold — ignore sub-threshold revolutions (sensor noise from stopped engines)
- v1.7.1 (seren fork) fix: default runningThreshold 5 -> 800 rpm (13.33 rev/s); inverter pickup on the tacho cable read up to ~8 Hz
