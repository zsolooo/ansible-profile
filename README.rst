===============
ansible-profile
===============

An Ansible plugin for timing tasks.


Usage
^^^^^

Features:
- Display times for each and every tasks that run
- Display 10 slowest task times
- Display aggregated role times
- The profiling is optional, it can be turned on with '-e profile=enabled' option for ansible-playbook command

.. code-block:: bash

    mkdir callback_plugins
    cd callback_plugins
    wget --no-check-certificates https://raw.githubusercontent.com/zsolooo/ansible-profile/master/callback_plugins/profile_tasks.py


Now, run your playbook with the '-e profile=enabled' option!

.. code-block:: bash

   ansible <args here> -e profile=enabled <playbook>
   <normal output here>
   PLAY RECAP ******************************************************************** 

   PLAY TIMINGS ****************************************************************** 
   common | update munin-node conf to allow remote connections ------------- 0.99s
   common | set up the dirsizes -------------------------------------------- 0.64s
   common | set up the weekly cron jobs ------------------------------------ 1.81s
   apache2 | enable default modules ---------------------------------------- 3.57s
   common | install custom fact -------------------------------------------- 0.93s
   common | update etc skel defaults --------------------------------------- 0.96s
   apache2-site | install the apache2 site --------------------------------- 0.89s
   common | copy over the backup script ------------------------------------ 1.09s
   apache2 | remove default apache configuration --------------------------- 1.94s
   apache2-site | enable the apache2 site ---------------------------------- 0.54s
   common | ufw allow munin trafic through --------------------------------- 1.59s
   apache2 | install the default site -------------------------------------- 0.76s
   apache2 | ufw allow http trafic through --------------------------------- 1.85s
   common | enable munin monitoring ---------------------------------------- 4.53s
   apache2 | update security configuration --------------------------------- 0.67s
   apache2 | make the configuration directories ---------------------------- 1.24s
   common | set up the daily cron jobs ------------------------------------- 1.39s
   common | create directory for ansible custom facts ---------------------- 1.01s
   apache2 | enable default site ------------------------------------------- 0.68s
   common | remove all messages of the day --------------------------------- 0.02s
   apache2 | install custom fact ------------------------------------------- 0.74s
   common | ensure that the archives directory exists ---------------------- 0.61s
   common | set up the hourly cron jobs ------------------------------------ 0.83s
   common | set the hostname ----------------------------------------------- 0.96s
   common | install the base packages -------------------------------------- 2.22s
   common | create the backup directories ---------------------------------- 6.27s
   common | create the scripts directory ----------------------------------- 6.14s
   common | set up the monthly rotation ------------------------------------ 1.62s
   common | synapticloop motd ---------------------------------------------- 0.02s
   apache2 | copy over the blank home packages ----------------------------- 0.71s
   common | copy over the default backup script ---------------------------- 9.14s
   apache2 | install the dependent packages -------------------------------- 1.60s
   apache2 | copy over the updated apache2 configuration ------------------- 0.71s
   common | create the etc skel directories -------------------------------- 0.73s
   common | disable munin monitoring items --------------------------------- 1.37s
   common | copy over munin configuration if munin-node is installed ------- 1.87s
   common | update nanorc file --------------------------------------------- 0.64s
   common | update system-watcher email ------------------------------------ 0.87s
   common | copy over munin monitoring if munin-node is installed ---------- 2.48s
   common | set up other cron jobs ----------------------------------------- 2.61s
   
   TOP 10 SLOWEST TASKS ********************************************************** 
   common | copy over the default backup script ---------------------------- 9.14s
   common | create the backup directories ---------------------------------- 6.27s
   common | create the scripts directory ----------------------------------- 6.14s
   common | enable munin monitoring ---------------------------------------- 4.53s
   apache2 | enable default modules ---------------------------------------- 3.57s
   common | set up other cron jobs ----------------------------------------- 2.61s
   common | copy over munin monitoring if munin-node is installed ---------- 2.48s
   common | install the base packages -------------------------------------- 2.22s
   apache2 | remove default apache configuration --------------------------- 1.94s
   common | copy over munin configuration if munin-node is installed ------- 1.87s
   
   ROLE TIMES ******************************************************************** 
   common  ---------------------------------------------------------------- 53.31s
   apache2  --------------------------------------------------------------- 14.48s
   apache2-site  ----------------------------------------------------------- 1.43s
   
   TOTAL TIME ******************************************************************** 
    ---------------------------------------------------------------------   69.22s
