.. _changelog:

ORBIT Changelog
===============

0.4.3
-----

- New feature: Cash flow and net present value calculation within
  ``ProjectManager``.
- Revised ``CustomArraySystemDesign`` module.
- Revised assumptions in ``MonopileDesign`` module to bring results in line
  with industry numbers.

0.4.2
-----

- New feature: Phase dependencies in ``ProjectManager``.
- New feature: Windspeed constraints at multiple heights, including automatic
  interpolation/extrapolation of configured windspeed profiles.
- Added option to define ``mobilization_days`` and ``mobilization_mult`` in a
  ``Vessel`` configuration file.
- Added option for pre-installation trenching operations to
  ``ArrayCableInstallation`` and ``ExportCableInstallation``.
- Revised ``OffshoreSubstationDesign`` to scale the size of the substations
  with the user-configured number of substations.
- Bugfix in the returned argument order of ``ProjectManager.run_install_phase``
  where the cost of a prior phase would be incorrectly applied as the elapsed
  time.

0.4.1
-----

- Modified installation to require version of marmot-agents that has an
  internal copy of simpy.
- Added/expanded ``detailed_outputs`` for all modules.
- Standardized naming of weight/mass terms to mass throughout the model.
- Cleanup in ``ProjectManager``.

0.4.0
-----

- Vessel mobilization added to all vessels in all installation modules.
  Defaults to 7 days at 50% day-rate.
- Cable lay, bury and simulataneous lay/bury methods are not flagged as
  suspendable to avoid unrealistic project delays.
- Cost of onshore transmission construction added to
  ``ExportCableInstallation``.
- Simplified ``ArrayCableInstallation``, ``ExportCableInstallation`` modules.
- Removed `pandas` from the internals of the model, though it is still useful
  for tabulating the project logs.
- Revised package structure. Functionally formerly in ORBIT.simulation or
  ORBIT.vessels has been moved to ORBIT.core.
- ``InstallPhase`` cleaned up and slimmed down.
- ``Environment`` and associated functionality has been replaced with
  ``marmot.Environment``.
- Logging functionality revised. No longer uses the base python logging module.
- ``Vessel`` now inherits from ``marmot.Agent``.
- Tasks that were in ``ORBIT.vessels.tasks`` have been moved to their
  respective modules and restructured with ``marmot.process`` and
  ``Agent.tasks``.
- Modules inputs cleaned up. ``type`` parameters are no longer required for
  monopile, transition piece or turbine component definitions.
- Removed old/irrelevant tests.

0.3.5
-----

- Added 'per kW' properties to ``ProjectManager`` CAPEX results.

0.3.4
-----

- Added configuration to ``ProjectManager`` that allows exceptions to be caught
  within individual modules and allows the project as a whole to continue.
- Fixed installation process when installing from GitHub.

0.3.3
-----

- Added configuration for multiple tower sections in ``TurbineInstallation``.
- Added configuration for seperate lay/burial in ``ArrayCableInstallation`` and
  ``ExportCableInstallation``.
- Overhauled test suite and associated library.
- Bugfix in ``CableCarousel``.
- Expanded WISDEM Fixed API.

0.3.2
-----

- Initial release of fixed substructure WISDEM API
- Material cost for monopiles and transition pieces added to ``MonopileDesign``
- Updated ``ProjectManager`` to allow user to override default ``DesignPhase``
  results
- Moved config validation to ``BasePhase`` and added call to
  ``self.validate_config`` for all current modules
- Config validation logic reworked so dicts of optional values are not
  required
- Added method to resolve project capacity in ``ProjectManager``. A user can
  now input ``plant.num_turbines`` and ``turbine.turbine_rating`` and
  ``plant.capacity`` will be added to the config.
- Added initial set of standardized inputs to ``ProjectManager``:

  - ``self.installation_capex``
  - ``self.installation_time``
  - ``self.project_days``
  - ``self.bos_capex``
  - ``self.turbine_capex``
  - ``self.total_capex``

0.3.1
-----

- Updated README
