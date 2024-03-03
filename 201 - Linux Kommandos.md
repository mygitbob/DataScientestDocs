---


---

<h2 id="basic-commands">Basic Commands</h2>
<p>fuer jeden Prozess wird ein pid File erzeugt in zB <code>/var/run/httpd/httpd.pid</code><br>
<code>echo -e "Neue Zeile\nausgeben"</code> ohne -e wird <strong>keine</strong> neue Zeile erzeugt<br>
<code>clear</code><br>
<code>sudo -i</code> interaktiver root modus, root wird mit <code>#</code> dargestellt, sonst <code>$</code><br>
<code>cd</code> ohne Parameter immer ins Home Verzeichnis<br>
<code>cat /etc/os-releases</code> Name &amp; Version des os<br>
<code>touch zehnfiles{1..10}.txt</code><br>
<code>cp -r dirname backdir</code> Verzeichnisse immer mit <code>-r</code> kopieren<br>
<code>rm -r dirname</code><br>
<code>mv</code> braucht kein <code>-r</code> fuer Verzeichnisse<br>
<code>mkdir -p /gibt/es/alle/noch/nicht</code><br>
<code>ln -s &lt;origin&gt; &lt;link-name&gt;</code><br>
<code>ls -t</code> bzw. <code>ls -tr</code> alle Files mit timestamp bzw. reversed<br>
<code>ls -d</code> Verzeichnisse nicht verfolgen<br>
<code>wc -l</code> count line numbers<br>
<code>tree &lt;dir&gt;</code><br>
<code>cat /etc/os-release</code><br>
<code>inxi -b</code> Systeminfo ( auf Ubuntu vorinstalliert )<br>
<code>lscpu</code><br>
<code>du -sh file_or_folder</code> Speicherverbrauch<br>
<code>open -a /Applications/Atom.app Vagrantfile</code> Textfile mit Editor oeffnen, macos<br>
<code>printenv</code> Umgebungsvaribalen anzeigen<br>
<code>tr 'zeichen_zum_ersetzen' 'neues_zeichen'</code><br>
zB <code>echo "aa,bb,cc" | tr ',' ':'</code> Ausgabe: aa:bb:cc</p>
<p><code>ps -ef | grep &lt;search term&gt; | tr -s " " | cut -d " " -f &lt;number&gt;</code> tr quescht die multiplen Leerzeichen der grep Ausgabe zusammen, dann kann ein " " als Delimiter benutzt werden</p>
<p><code>tee</code>, used with a pipe, <strong>reads standard input, then writes the output of a program to standard output and simultaneously  copies  it into the specified file or files</strong>. Use the tee command to view your output immediately and at the same time, store it for future use.</p>
<p><code>lsb-release</code> <strong>ist ein einfaches Werkzeug, das hilft, die benutzte Linux-Distribution zu identifizieren und die Einhaltung der Linux Standard Base zu prüfen</strong>. Es wird keine LSB-Übereinstimmung angezeigt, solange die erforderlichen Metapakete nicht installiert sind.</p>
<p><code>nohub</code> Nohup, short for no hang up is a command in Linux systems that <strong>keep processes running even after exiting the shell or terminal</strong>. Nohup prevents the processes or jobs from receiving the SIGHUP (Signal Hang UP) signal. This is a signal that is sent to a process upon closing or exiting the terminal.</p>
<p><code>mount -a</code> 		checken ob alles ok<br>
<code>mount -fav</code>	wie oben aber mit nfs mount</p>

<table>
<thead>
<tr>
<th>history</th>
<th></th>
</tr>
</thead>
<tbody>
<tr>
<td><code>history n</code></td>
<td>zeige die letzten n Eintraege an</td>
</tr>
<tr>
<td><code>echo $HISTSIZE</code></td>
<td>entspricht der Eintrage in history</td>
</tr>
<tr>
<td><code>!!</code></td>
<td>last command</td>
</tr>
<tr>
<td><code>!n</code></td>
<td>command with number n in history</td>
</tr>
<tr>
<td><code>!!:s/before/after</code> auch als <code>!n:s/bla...</code></td>
<td>last command with substitution</td>
</tr>
<tr>
<td><code>unset HISTFILE &amp;&amp; exit</code></td>
<td>keine Befehle der aktuellen Session speichern</td>
</tr>
<tr>
<td><code>HISTIGNORE</code></td>
<td>welche Kommandos sollen nicht eingetragen werden</td>
</tr>
<tr>
<td><code>$_</code></td>
<td>das letzte Argument</td>
</tr>
<tr>
<td><code>alias &lt;aliasname&gt;=&lt;command&gt;</code></td>
<td></td>
</tr>
</tbody>
</table><h3 id="cronjob">cronjob</h3>
<pre><code>crontab -e
</code></pre>
<p>MM HH DOM (Day of Month) mm DOW (Day of Week)<br>
entweder Wert, Bereich zB 1-5 oder *</p>
<h2 id="networking-commands">Networking commands</h2>
<pre><code>ifconfig
ip addr shows
ping &lt;host&gt;
/etc/hosts # ip addr Namen zuweisen
tracert &lt;host&gt; 	#std 3 Pakete verschicken
netstat -antp 	#alle offenen port
ss -tunlp 		#ersetyt netstat
nmap &lt;host&gt; 	#show open ports
dig &lt;url&gt; 		#dns info
route -n		#show gateways
arp				#mac table anzeigen
mtr &lt;host&gt; 	#hops inkl. package loss, im Ggs. zu tracert dynamisch
telnet &lt;host&gt; &lt;port&gt;	#gucken ob port offen ist 	
</code></pre>
<h2 id="file-types">File Types</h2>
<p><code>file &lt;filename&gt;</code> outputs filetype<br>
<strong><code>d</code> directory</strong><br>
<strong><code>l</code> link</strong><br>
<strong><code>c</code> character file</strong> zB. keyboard in <code>/dev</code><br>
<strong><code>b</code> block file</strong> zB.harddisk in <code>/dev</code><br>
<strong><code>-</code> normal file</strong></p>
<h2 id="filters">Filters</h2>
<h3 id="output">output</h3>
<p><code>cat</code><br>
<code>less</code> : <code>/</code> for searching<br>
<code>head -n</code> first n lines<br>
<code>tail -n</code> last n lines<br>
<code>tail -f</code> updates changes</p>
<h4 id="filters-1">filters</h4>
<p><code>grep &lt;tofind&gt; &lt;filename&gt;</code><br>
<code>grep -i</code> not case sensitiv<br>
<code>grep -R</code> look in folders<br>
<code>grep -v</code> invert/negate<br>
<code>grep -c</code> counts occurreance</p>
<p><code>cut -d&lt;delimiter_symbol&gt; -f&lt;filed_number&gt; &lt;filename&gt;</code><br>
<code>awk -F':' '{print $1}'</code> same as <code>cut</code> above<br>
<code>sed -i 's/&lt;search_term&gt;/&lt;replacement&gt;/g' *</code> , -i needed to save changes app<br>
<code>find /etc -name host*</code><br>
<code>locate</code> oder <code>mlocate</code> vorher <code>updatedb</code></p>
<h3 id="prozesse">Prozesse</h3>
<p>stoppen: <code>ctrl + z</code><br>
weitermachen <code>fg</code><br>
im Hintergrund starten: <code>name_des_kommandos &amp;</code><br>
PID eines Programms ermitteln: <code>pidof Process_Name</code><br>
bessere top Version: <code>htop</code></p>
<h2 id="redirections">Redirections</h2>
<p><code>&gt;</code> replace output file, Achtung nur der StdOut wird hiermit umgeleitet<br>
<code>&gt;&gt;</code> append output file<br>
<code>cat /dev/null &gt; file_content_to_be_deleted</code><br>
<code>command 1&gt;&gt;</code> redirect stdoutput<br>
<code>command 2&gt;&gt;</code> redirect stderror<br>
<code>command &amp;&gt;&gt;</code> redirect all<br>
<code>command &gt; file 2&gt;&amp;1</code> hier wird der StdError in die selbe Datei wie StdOut umgeleitet<br>
<code>&lt;</code> input file</p>
<h2 id="users-and-groups">Users and Groups</h2>
<p>users in <code>/etc/passwd</code><br>
groups in <code>/etc/group</code><br>
<code>id &lt;user&gt;</code> information about user<br>
<code>useradd &lt;uname&gt;</code> create new user<br>
<code>usermod -aG &lt;gname&gt; &lt;uname&gt;</code> for 2nd group or <code>usermod -ag &lt;gname&gt; &lt;uname&gt;</code> for 1st group<br>
<code>groupadd &lt;gname&gt;</code><br>
<code>passwd &lt;uname&gt;</code><br>
<code>su - &lt;uname&gt;</code> change identity<br>
<code>lsof -u &lt;uname&gt;</code> show all files opened by user<br>
<code>userdel -r &lt;uname&gt;</code> delete user and his home dir<br>
<code>groupdel &lt;gname&gt;</code> delete group</p>
<h2 id="file-permissions">File Permissions</h2>
<p>link permissions != link destination permissions<br>
<code>chown &lt;uname&gt;:&lt;ganme&gt; &lt;file or dir&gt;</code> -R vist all folders<br>
<code>chmod o-x &lt;file or dir&gt;</code> remove execution for group others<br>
<code>chmod g+w &lt;file or dir&gt;</code> add write permission for groupvagrant up<br>
<code>chmod +</code> oder <code>chmod -</code> gilt fuer alle Benutzer, alternativ auch a<br>
–reference nimmt ein file als Blaupause fuer die Rechte<br>
-R rekursiv<br>
4 read<br>
2 write<br>
1 execute<br>
<code>chmod 770 &lt;file&gt;</code> alle Rechte fuer den Bentuzer &amp; ide Gruppe, keine fuer others</p>
<h2 id="sudo">Sudo</h2>
<p><code>sudo -i</code> wede superuser<br>
<code>visudo</code> oeffnet die sudoers Datei mit entsprechenden Rechten<br>
Fehleranfaellig bei manuellen Aenderungen !<br>
besser Datei in <code>/etc/sudoers.d</code> anlegen, 1.Eintrag<code>%&lt;groupname&gt;</code> oder <code>&lt;uname&gt;</code><br>
im sudoers file kann <code>NOPASSWORD:ALL</code> eingetragen werden, dann muss kein pw eingegeben werden</p>
<h2 id="packet-management">Packet Management</h2>
<p><code>curl &lt;url of rpm&gt; -o &lt;give it a name&gt;</code> -o um die Ausgabe als Datei zu speichern<br>
<code>wget &lt;url of rpm&gt;</code></p>

<table>
<thead>
<tr>
<th>rpm-command</th>
<th></th>
</tr>
</thead>
<tbody>
<tr>
<td><code>rpm -ivh &lt;package&gt;</code> –</td>
<td>-ivh install verbose human readable  –</td>
</tr>
<tr>
<td><code>rpm -qa</code> –</td>
<td>alle installierten Pakete anzeigen–</td>
</tr>
<tr>
<td><code>rpm -qi &lt;package&gt;</code></td>
<td>detaillierte Informationen</td>
</tr>
<tr>
<td><code>rpm -qf &lt;path to file&gt;</code></td>
<td>zu welchem Package gehoert die Datei</td>
</tr>
<tr>
<td><code>rpm -qc &lt;package&gt;</code></td>
<td>Liste der Konfigurationsdateien</td>
</tr>
<tr>
<td><code>rpm -e &lt;package name&gt;</code></td>
<td>Paket loeschen</td>
</tr>
</tbody>
</table>
<table>
<thead>
<tr>
<th>yum</th>
<th></th>
</tr>
</thead>
<tbody>
<tr>
<td><code>yum search &lt;package&gt;</code></td>
<td>search available repositories in <code>/etc/yum.repos.d/</code></td>
</tr>
<tr>
<td><code>yum -y install &lt;package&gt;</code></td>
<td></td>
</tr>
<tr>
<td><code>yum reinstall &lt;package&gt;</code></td>
<td></td>
</tr>
<tr>
<td><code>yum remove &lt;package&gt;</code></td>
<td></td>
</tr>
<tr>
<td><code>yum update</code></td>
<td>updates all packages</td>
</tr>
<tr>
<td><code>yum grouplist</code></td>
<td>shows all packages of a group</td>
</tr>
<tr>
<td><code>yum groupinstall &lt;groupname&gt;</code></td>
<td>installs all packages of a group</td>
</tr>
<tr>
<td><code>yum repolist</code></td>
<td></td>
</tr>
<tr>
<td><code>yum clean all</code></td>
<td></td>
</tr>
<tr>
<td><code>yum history</code></td>
<td></td>
</tr>
<tr>
<td><code>yum --enablerepo=&lt;reponame&gt; install &lt;package&gt;</code></td>
<td>use specified repo and install package</td>
</tr>
<tr>
<td><code>yum info &lt;package&gt;</code></td>
<td></td>
</tr>
</tbody>
</table>
<table>
<thead>
<tr>
<th>dpkg</th>
<th></th>
</tr>
</thead>
<tbody>
<tr>
<td><code>dpkg -i|--install deb_packagename</code></td>
<td></td>
</tr>
<tr>
<td><code>dpkg -s|--status package_name</code></td>
<td></td>
</tr>
<tr>
<td><code>dpkg -r|--remove package_name</code></td>
<td></td>
</tr>
<tr>
<td><code>dpkg -P|--purge package_name</code></td>
<td>remove package and its configuration files</td>
</tr>
<tr>
<td><code>dpkg -l</code></td>
<td>list all installed packages and their status</td>
</tr>
<tr>
<td><code>dpkg -c|--contents deb_packagefile</code></td>
<td></td>
</tr>
<tr>
<td><code>dpkg -I|--info deb_packagename</code></td>
<td>get info before installation</td>
</tr>
<tr>
<td><code>dpkg -x deb_packagename /path/to/directory</code></td>
<td>extrect all packeage files, <code>-X</code> will also show them after extracting</td>
</tr>
<tr>
<td><code>dpkg --unpack deb_packagename</code></td>
<td>unpack but do not install</td>
</tr>
<tr>
<td><code>dpkg --configure package_name</code></td>
<td>reconfigure unpacked package</td>
</tr>
<tr>
<td><code>dpkg -C|--audit package_name</code></td>
<td>search for partially installed packages</td>
</tr>
<tr>
<td><code>dpkg -L package_name</code></td>
<td>list all files of an installed package</td>
</tr>
<tr>
<td><code>dpkg -S filename_pattern</code></td>
<td>search for file/path-pattern in installed packages</td>
</tr>
<tr>
<td><code>dpkg --clear-avail</code></td>
<td>erase existing information about what packages are available</td>
</tr>
</tbody>
</table>
<table>
<thead>
<tr>
<th>apt</th>
<th>cache located at <code>/var/cache/apt/archives/</code></th>
</tr>
</thead>
<tbody>
<tr>
<td><code>sudo apt-get [--reinstall] install [package-name]</code></td>
<td></td>
</tr>
<tr>
<td><code>sudo apt-get remove [package-name]</code></td>
<td></td>
</tr>
<tr>
<td><code>sudo apt-get purge [package-name]</code></td>
<td></td>
</tr>
<tr>
<td><code>sudo apt-get update</code></td>
<td>fetch and re-index all packages, immer vor Installation aufrufen !?</td>
</tr>
<tr>
<td><code>sudo apt-get upgrade</code></td>
<td>for all packages, beware !</td>
</tr>
<tr>
<td><code>apt-cache pkgnames</code></td>
<td>list all packages</td>
</tr>
<tr>
<td><code>apt-cache show [package-name]</code></td>
<td>info about package</td>
</tr>
<tr>
<td><code>apt-cache search &lt;search term&gt;</code></td>
<td>searches in name, description and provides</td>
</tr>
<tr>
<td><code>/etc/apt/sources.list</code></td>
<td>repositories</td>
</tr>
</tbody>
</table><h2 id="services">Services</h2>
<p><code>/etc/systemd</code> config files</p>

<table>
<thead>
<tr>
<th>Viewing Systemd Information</th>
<th></th>
</tr>
</thead>
<tbody>
<tr>
<td><code>systemctl list-dependencies</code></td>
<td>Show a unit’s dependencies</td>
</tr>
<tr>
<td><code>systemctl list-sockets</code></td>
<td>List sockets and what activates</td>
</tr>
<tr>
<td><code>systemctl list-jobs</code></td>
<td>View active systemd jobs</td>
</tr>
<tr>
<td><code>systemctl list-unit-files</code></td>
<td>See unit files and their states</td>
</tr>
<tr>
<td><code>systemctl list-units</code></td>
<td>Show if units are loaded/active</td>
</tr>
<tr>
<td><code>systemctl get–default</code></td>
<td>List default target (like run level)</td>
</tr>
</tbody>
</table>
<table>
<thead>
<tr>
<th>Working with Services</th>
<th></th>
</tr>
</thead>
<tbody>
<tr>
<td><code>systemctl status &lt;service&gt;</code></td>
<td></td>
</tr>
<tr>
<td><code>systemctl stop service</code></td>
<td>Stop a running service</td>
</tr>
<tr>
<td><code>systemctl start service</code></td>
<td>Start a service</td>
</tr>
<tr>
<td><code>systemctl restart service</code></td>
<td>Restart a running service</td>
</tr>
<tr>
<td><code>systemctl reload service</code></td>
<td>Reload all config files in service</td>
</tr>
<tr>
<td><code>systemctl status service</code></td>
<td>See if service is running/enabled</td>
</tr>
<tr>
<td><code>systemctl enable service</code></td>
<td>Enable a service to start on boot</td>
</tr>
<tr>
<td><code>systemctl disable service</code></td>
<td>Disable service–won’t start at boot</td>
</tr>
<tr>
<td><code>systemctl show service</code></td>
<td>Show properties of a service (or other unit)</td>
</tr>
<tr>
<td><code>systemctl -H host status network</code></td>
<td>Run any systemctl command remotely</td>
</tr>
<tr>
<td><code>systemctl is-active</code></td>
<td></td>
</tr>
<tr>
<td><code>systemctl is-enabled</code></td>
<td></td>
</tr>
</tbody>
</table>
<table>
<thead>
<tr>
<th>Changing System States</th>
<th></th>
</tr>
</thead>
<tbody>
<tr>
<td><code>systemctl reboot</code></td>
<td>Reboot the system (reboot.target)</td>
</tr>
<tr>
<td><code>systemctl poweroff</code></td>
<td>Power off the system (poweroff.target)</td>
</tr>
<tr>
<td><code>systemctl emergency</code></td>
<td>Put in emergency mode (emergency.target)</td>
</tr>
<tr>
<td><code>systemctl default</code></td>
<td>Back to default target (multi-user.target)</td>
</tr>
</tbody>
</table>
<table>
<thead>
<tr>
<th>Viewing Log Messages</th>
<th></th>
</tr>
</thead>
<tbody>
<tr>
<td><code>journalctl</code></td>
<td>Show all collected log messages</td>
</tr>
<tr>
<td><code>journalctl -u network.service</code></td>
<td>See network service messages</td>
</tr>
<tr>
<td><code>journalctl -f</code></td>
<td>Follow messages as they appear</td>
</tr>
<tr>
<td><code>journalctl -k</code></td>
<td>Show only kernel messages</td>
</tr>
</tbody>
</table><h2 id="processes">Processes</h2>
<p><code>top</code>, <code>htop</code>, <code>ps aux</code>, <code>ps -ef</code> parent process id<br>
<code>kill &lt;pid&gt;</code>, <code>kill -9 &lt;pid&gt;</code></p>
<h2 id="archives">Archives</h2>
<p><code>tar -czvf &lt;tar file&gt; &lt;dir&gt;</code> einpacken<br>
<code>tar -xzvf &lt;file&gt; [-C &lt;path&gt;]</code> auspacken<br>
<code>zip -rf &lt;zip file&gt; &lt;source&gt;</code><br>
<code>unzip &lt;zip file&gt;</code></p>
<h2 id="ubuntu-commands">Ubuntu commands</h2>
<p><code>useradd</code> legt kein Heimatverzeichnis bzw. spooler, statt dessen <code>adduser</code> verwenden<br>
<code>visudo</code> startet nano, <code>export EDITOR=vim</code> fuer temporaeren Wechsel<br>
installierte Dienste werden automatisch gestartet &amp; eventuell Firewall angepasst</p>

