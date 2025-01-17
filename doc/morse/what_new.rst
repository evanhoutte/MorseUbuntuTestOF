What's new in MORSE 1.4?
========================

General
-------

Components
----------

Robots
++++++

Actuators
+++++++++

- the :doc:`user/actuators/orientation` actuator has been enhanced to possibly
  work more realistically, by limiting the speed of the rotations. The default
  is still to go directly to the desired orientation.

Sensors
+++++++

- **longitude**, **latitude** and **altitude** are not anymore properties of
  :doc:`user/sensors/gps` but must be set at the environment level.

Modifiers
+++++++++

- Introduce ECEF and Geodetic modifiers, allowing to convert coordinates from
  Blender world to ECEF-r or Geodetic coordinates (and vice-versa). It should
  improve interoperability with flight systems in general.
- Introduce Feet modifier, to convert imperial units to meter buts (and
  vice-versa)

Middlewares
-----------

General
+++++++


Builder API
-----------

API addition
++++++++++++

Pymorse
-------

- Robots created in loop are handled smartly. They are still usable as
  previously, but it is also possible to access them using the list foos (if
  your robot name is foo) (`#358  <https://github.com/morse-simulator/morse/issues/358>`_).
- Streams are now created lazily, fixing control with large number of robots /
  sensors (`#626  <https://github.com/morse-simulator/morse/issues/626>`_).


What's new in MORSE 1.3?
========================

General
-------

Components
----------

Robots
++++++

Actuators
+++++++++

- Introduce the new actuator :doc:`user/actuators/arucomarker`, allowing to
  simulate the ArUco augmented-reality marker.

Sensors
+++++++

- The timestamp field is now in seconds instead of milliseconds (`#498 <https://github.com/morse-simulator/morse/issues/498>`_)
- :doc:`user/sensors/semantic_camera` gains two properties (`#396 <https://github.com/morse-simulator/morse/issues/396>`_):
    - `tag` allows to restrict the kind of object you want to detect
    - `relative` returns the position information of the various objects from
      the camera sensor frame (and not the global frame).

- :doc:`user/sensors/laserscanner` gain the possibility to return also a
  remission value at the `rssi` level.
- Introduce the new sensor :doc:`user/sensors/radar_altimeter`, allowing to
  retrieve the distance to the ground.
- Improvement of :doc:`user/sensors/accelerometer`, :doc:`user/sensors/imu`
  and :doc:`user/sensors/velocity`. They now works properly with robots with
  or without physics, and returns properly information in the sensor frame.
  The computation method is configurable using the `ComputationMode` property,
  counterpart of the `ControlType` in several actuators.
- Introduce the new sensor :doc:`user/sensors/barometer`, allowing to compute
  the atmospheric pressure.

Middlewares
-----------

General
+++++++

- Each datastream manager now get an action handler, allowing them to run some
  specific middleware behaviour once by simulation turn.

Socket
++++++

- Socket middleware now accepts the keyword 'port' to specify on which port
  you want the socket binds itself.
- It is now possible to synchronise with an external clock using the socket
  middleware. See the documentation of **time_sync** in
  :doc:`user/middlewares/socket`.

Moos
++++

- Support for Moos has been enhanced, allowing to use multiples Moos nodes.
  Moreover, it supports additional actuators such as
  :doc:`user/actuators/teleport` and :doc:`user/actuators/light`.

HLA
+++

- HLA can be now used as a general purpose middleware, i.e. it is possible to
  import / export any actuator / sensor using the HLA interface. Through, for
  moment, no Simulation Object Model (SOM) has been formally defined for
  Morse.


Builder API
-----------

API addition
++++++++++++

- Add a method ``Environment.configure_stream_manager`` allowing to pass
  option/information to each datastream manager.
- It is now possible to control the mist settings in Morse, using
  ``Environment.enable_mist`` and ``Environment.set_mist_settings``.

Previous releases
-----------------

.. toctree::
    :maxdepth: 1	

    releasenotes/1.2
    releasenotes/1.1
    releasenotes/1.0
    releasenotes/0.6
    releasenotes/0.5
    releasenotes/0.4
