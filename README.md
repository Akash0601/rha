Overview of Container Technology
Objectives

After completing this section, students should be able to describe the difference between container applications and 
traditional deployments.

Containerized Applications

Software applications typically depend on other libraries, configuration files, or services that are provided by the runtime
environment. The traditional runtime environment for a software application is a physical host or virtual machine, and
application dependencies are installed as part of the host.

For example, consider a Python application that requires access to a common shared library that implements the TLS protocol.
Traditionally, a system administrator installs the required package that provides the shared library before installing the
Python application.

The major drawback to traditionally deployed software application is that the application's dependencies are entangled with
the runtime environment. An application may break when any updates or patches are applied to the base operating system (OS).

For example, an OS update to the TLS shared library removes TLS 1.0 as a supported protocol. This breaks the deployed Python
application because it is written to use the TLS 1.0 protocol for network requests. This forces the system administrator to
roll back the OS update to keep the application running, preventing other applications from using the benefits of the updated
package. Therefore, a company developing traditional software applications may require a full set of tests to guarantee that
an OS update does not affect applications running on the host.

Furthermore, a traditionally deployed application must be stopped before updating the associated dependencies. To minimize 
application downtime, organizations design and implement complex systems to provide high availability of their applications.
Maintaining multiple applications on a single host often becomes cumbersome, and any deployment or update has the potential 
to break one of the organization's applications.

!images/123.png

Alternatively, a software application can be deployed using a container . A container is a set of one or more processes that
are isolated from the rest of the system. Containers provide many of the same benefits as virtual machines, such as security,
storage, and network isolation. Containers require far fewer hardware resources and are quick to start and terminate. 
They also isolate the libraries and the runtime resources (such as CPU and storage) for an application to minimize the impact
of any OS update to the host OS, as described in Figure 1.1: Container versus operating system differences .

The use of containers not only helps with the efficiency, elasticity, and reusability of the hosted applications, but also
with application portability. The Open Container Initiative provides a set of industry standards that define a container
runtime specification and a container image specification. The image specification defines the format for the bundle of 
files and metadata that form a container image. When you build an application as a container image, which complies with 
the OCI standard, you can use any OCI-compliant container engine to execute the application.

There are many container engines available to manage and execute individual containers, including Rocket, Drawbridge, LXC,
Docker, and Podman. Podman is available in Red Hat Enterprise Linux 7.6 and later.
