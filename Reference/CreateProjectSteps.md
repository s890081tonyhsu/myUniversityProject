A new project is created by following these steps:
====

File, Folder Create
----

  - Create a new project directory inside netfpga/projects

  - Update the ``NF_DESIGN_DIR`` directory to point to the new project directory. 

Example (Bourne shell syntax): ``export NF_DESIGN_DIR=$(HOME)/netfpga/projects/my_first_project`` (See the guide for more information.)

  - Create the following directories inside the project directory: ``include``, ``src``, ``synth``, and ``test``.

Optionally create ``doc``, ``lib``, and ``sw``. (Note: ``lib`` will be automatically created when the register generation tool is run.)

  - Create a ``project.xml`` file inside the include directory. See the Register System section below for more information.

  - Add any library modules to the ``project.xml`` file.

  - Write any project-specific Verilog and place inside the src directory.

  - Write module-specific XML files for any new modules you have written and place in the include directory.


Write Verilog code (For hardware) and C code (For test)
----
  - In the new python testing infrastructure, simulation and hardware (previously regression) tests have been unified, so a test can be written once and run as either a simulation or hardware test, unless hardware specific functions are needed. Tests should be placed in a project's test directory. Test directories should be named ``both_<major>_<minor>`` if they can be run in both simulation and hardware, ``hw_<major>_<minor>`` if the test can only be run as a hardware test, and ``sim_<major>_<minor>``; if the test can only be run as a simulation test. Neither major or minor can have underscores in the name, nor can they be blank.

  - Copy the Makefile from the reference router ``synth`` directory into your ``synth`` directory.

  - Synthesize the design by running make inside the synth directory.

Test and Run
----

  - Write hardware tests and place them in the test directory. Run with nf_test.py (See Verification for more information.)

  - Write any software and place inside the ``sw`` directory.

  - Add documentation to the ``doc`` directory.

  - Contribute your project if you think your project may be useful to others. See the Develop page for more information.

Note: The act of running simulations or synthesizing the project causes the registers to be regenerated. Use the ``nf_register_gen.pl`` tool if you want to regenerate registers without running simulation/synthesis.
