This is a page for frequently asked questions and for known limitations
of OpenCMISS.


**Question**:

    What is the purpose of the OpenCMISS Developers weekly conference calls?

**Answer**:

    The purpose of the OpenCMISS Developers weekly conference call is to
    update other members on your progress and what you intend to do next. It
    is a forum in which general questions and points can be raised.


**Question**:

    How do I get included in the OpenCMISS Developers weekly conference
    calls?

**Answer**:

    Currently \_Skype\_ is being used for the weekly conference calls. The
    conference calls are held mid-week, because the participants are based
    across multiple time zones the times of the conference switch as the
    time zones change. If you would like to be included in the weekly
    conference calls, send an email to
    opencmiss-developers@lists.sourceforge.net including your \_Skype\_
    name.

**Question**:

    What is the current time of the OpenCMISS Developers weekly conference
    call?

**Answer**:

    Germany Wednesday 20:00
    New Zealand Thursday 08:00
    Norway Wednesday 20:00
    Spain Wednesday 20:00
    UK Wednesday 19:00


**Question**:

    How do I obtain and install the TotalView debugger?

**Answer**:

    You will need to first install download and unpack the TotalView
    executables and library files from the TotalView website
    [www.totalviewtech.com](http://www.totalviewtech.com/). You will then
    need to obtain a license file from TotalView. Finally you will need to
    add the following to your local .bashrc file:

    export LM\_LICENSE\_FILES=&lt;LOCATION OF flexlm-10.8.0-3 FOLDER&gt;

    export PATH=&lt;LOCATION OF TOTALVIEW BIN FOLDER&gt;:${PATH}





\\ \_\*\*11\\\\. Question:\*\*\_\\ \\ How do I perform a runtime memory
profile of an executable using Valgrind? \\ \\ \_\*\*Answer:\*\*\_\\ \\
1\\\\. Compile the program you would to profile \\ \\ 2\\\\. Run the
executable of program using the command: \_valgrind --tool=massif
--time-unit=B program\_executable\_name\_\\ \\ 3\\\\. Once run, type the
command (where: NNNN is a process number): \_ms\_print massif.out.NNNN >
massif.out.NNNN.txt\_\\ \\ 4\\\\. The memory profile will be contained
in the file: \_massif.out.NNNN.txt\_\\ \\

`` \``

\\ \\

-

   -

      -  \\

\\ \_\*\*12\\\\. Question:\*\*\_\\ \\ I now want to perform a runtime
memory profile of an executable using Valgrind running mpiexec across a
number of cores on a multicore desktop machine? \\ \\
\_\*\*Answer:\*\*\_\\ \\ 1\\\\. In your home directory create a blank
\_mpd.hosts\_ file. Then on consecutive lines in this file enter the
location of the core on which the job is going to run. So for example,
if we want to use 8 cores on the local machine, we would enter
\_LOCALHOST\_ on 8 consecutive lines at the top of the file. \\ \\
2\\\\. In your home directory create a \_.mpd.conf\_ file with the
contents of: \_PD\_SECRETWORD=\_ANY\_WORD \\ \\ 3\\\\. Now set the mpi
daemon running in the background: \_mpd &\_\\ \\ 4\\\\. Go to the
program directory and compile the program you would to profile with:
\_make DEBUG=false\_\\ \\ 5\\\\. Run the executable of program using the
command (where N is the number of cores to be used): \_mpiexec -n N
valgrind --tool=massif --time-unit=B program\_executable\_name \_\\ \\ }
