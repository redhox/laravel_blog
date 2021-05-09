
<h1> instalation et deploiment d'un site d'article laravel </h1>
<br>
le "laravel_blog" est le resulta du tuto de "bestmomo" present <a href="https://laravel.sillo.org/laravel-8/">ici</a>
<br>
<br>
Depandance: <br>
&emsp; -<a href="https://doc.ubuntu-fr.org/lamp">php</a> (BCMath, Ctype, JSON, Mbstring, OpenSSL, PDO, Tokenizer, and XML)<br>
&emsp; -mysql ou mariadb <br>
&emsp; -npm (<a href="https://www.geeksforgeeks.org/how-to-update-npm/" alt="npm install -g npm@next">a jour</a>) <br>
&emsp; -composer <br>
&emsp; -git (optionnelle) <br>


<h2>instalation</h2>
tuto de:https://medium.com/@xroms123/laravel-clone-project-9e4eca817057
                
        tellecharger le depot
            # git clone https://github.com/redhox/laravel_blog.git 

        dans le dossier:
            Install composer: 
                        # composer install

        Install npm package:
                        # npm install

        copier et edité .env file from .env.example:
                        # cp .env.example .env
        "crée une database dont le nom et les accès seront dans le .env"

        Generé la project key:
                        # php artisan key:generate
                        
        faite la migration: des table:
                        # php artisan migrate

        start project:
                        # php artisan serve
                        
                        
<h2>deploiment du projet :</h2>
"sur une machine debian"
<br>
tuto de:https://tecadmin.net/install-laravel-on-debian-10-buster/ 
<br>
dans   "etc/apache2/sites-available/000-default.conf"   configuré le vrtual_host
<br>
"/var/www/votre_projet_laravel" etant le repertoire de base pour les projet web sous debian 
<br>

        <VirtualHost *:80>

                ServerAdmin webmaster@localhost
                DocumentRoot /var/www/votre_projet_laravel/public

                <Directory />
                        Options FollowSymLinks
                        AllowOverride None
                </Directory>
                <Directory /var/www/votre_projet_laravel>
                        AllowOverride All
                </Directory>

                ErrorLog ${APACHE_LOG_DIR}/error.log
                CustomLog ${APACHE_LOG_DIR}/access.log combined

        </VirtualHost>
        
puis pour finir recharger apache: 

        sudo service apache2 restart

<h2> droit des dossier sous unix: </h2>
(evité le chmod -R 777) <br>
tuto de:https://stackoverflow.com/questions/30639174/how-to-set-up-file-permissions-for-laravel
        

 
         sudo chown -R www-data:www-data /var/www/votre_projet_laravel
         sudo find /var/www/votre_projet_laravel -type f -exec chmod 644 {} \;   
         sudo find /var/www/votre_projet_laravel -type d -exec chmod 755 {} \;
                        
puis dans la racine du dossier laravel:
    
        sudo chown -R $USER:www-data .
        
        sudo find . -type f -exec chmod 664 {} \;   
        sudo find . -type d -exec chmod 775 {} \;
