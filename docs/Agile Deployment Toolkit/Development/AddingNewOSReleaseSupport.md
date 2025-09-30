For all new operating systems that are added, the quick spec and the main spec will need to be updated and you might like to also make the new
version the default version for in your templates themselves.

#### CODE CHANGES WITH NEW OS RELEASES

I have written things to be as frictionless as possible but there is one case where whenever there is a new Debian OS release there needs to be a minor 
code change update

In the files GetOperatingSystemVersion on the build-machine scripts and the autoscaler scripts for the Exoscale provider, there needs to be an 
update for the new debian version following the example pattern below:

>     if ( [ "${BUILDOS_VERSION}" = "12" ] )
>     then
>         /bin/echo "Linux Debian ${BUILDOS_VERSION} (Bookworm) 64-bit"
>     elif ( [ "${BUILDOS_VERSION}" = "13" ] )
>     then
>          /bin/echo "Linux Debian ${BUILDOS_VERSION} (Trixie) 64-bit"
>     fi

Debian 13 is the current release and so to make the update to support Debian 14 when it is released the following code will be needed>     

>     if ( [ "${BUILDOS_VERSION}" = "12" ] )
>     then
>         /bin/echo "Linux Debian ${BUILDOS_VERSION} (Bookworm) 64-bit"
>     elif ( [ "${BUILDOS_VERSION}" = "13" ] )
>     then
>          /bin/echo "Linux Debian ${BUILDOS_VERSION} (Trixie) 64-bit"
>     elif ( [ "${BUILDOS_VERSION}" = "14" ] )
>     then
>          /bin/echo "Linux Debian ${BUILDOS_VERSION} (Forky) 64-bit"
>     fi

