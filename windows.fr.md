# Instructions de configuration

Les instructions ci-dessous vont te permettre de configurer ton ordinateur pour [la formation Développement Web du Wagon](https://www.lewagon.com/web-development-course/full-time).

**Lis-les attentivement et exécute toutes les commandes dans l’ordre suivant**. En cas de blocage, n’hésite pas à demander au prof :raising_hand:

C’est parti :rocket:

## Version de Windows

Avant de commencer, on va vérifier que la version de Windows installée sur ton ordinateur est compatible avec ces instructions de configuration.

### Windows 10 ou Windows 11

Pour pouvoir configurer ton ordinateur, **Windows 10 ou Windows 11** doit être installé dessus.

Pour connaître ta version de Windows :
- Appuie sur `Windows` + `R`
- Saisis `winver`
- Appuie sur `Enter`

:heavy_check_mark: Si les premiers mots qui apparaissent dans cette fenêtre sont **Windows 10 ou Windows 11**, c’est bon :+1:

:x: Sinon, tu ne pourras pas utiliser cette configuration. Il faut que tu mettes à jour ton Windows à la version 10 :point_down:

<details>
  <summary>Mise à niveau vers Windows 10</summary>

  - Télécharge Windows 10 depuis [Microsoft](https://www.microsoft.com/fr-fr/software-download/windows10)
  - Installe-le. L’installation devrait prendre une heure environ, mais cela dépend de ton ordinateur
  - Une fois l’installation terminée, exécute les commandes ci-dessus pour vérifier que tu es sous **Windows 10**
</details>

:information_source: [La mise à jour Windows 11 est toujours en cours de déploiement](https://www.microsoft.com/en-us/windows/get-windows-11), ce qui signifie qu'elle peut être disponible, ou pas, pour ton ordinateur.

:warning: **Si tu as Windows 10 installé, tu n'as pas besoin de faire la mise à jour Windows 11 pour continuer cette configuration**.

### Dernières mises à jour

Une fois que tu as vérifié que tu utilises Windows 10 ou 11, tu vas devoir installer les dernières mises à jour.

Ouvre Windows Update :
- Appuie sur `Windows` + `R`
- Saisis `ms-settings:windowsupdate`
- Appuie sur `Enter`
- Clique sur « Rechercher les mises à jour »

:heavy_check_mark: Si tu vois apparaître une coche verte et le message « Vous êtes à jour », c’est bon :+1:

:warning: Si tu vois apparaître un point d’exclamation rouge et le message « Mise à jour disponible », installe-la et recommence jusqu’à ce que le message « Vous êtes à jour » apparaisse :loop:

:x: Si tu vois apparaître un message d’erreur indiquant que Windows ne peut pas appliquer les mises à jour, **demande au prof**.

<details>
  <summary>Activer le service Windows Update pour corriger les mises à jour</summary>

  Certains antivirus et logiciels désactivent le service de mise à jour dont on a besoin, entraînant l’erreur que tu vois apparaître. On va corriger ça !
  - Appuie sur `Windows` + `R`
  - Saisis `services.msc`
  - Appuie sur `Enter`
  - Double-clique sur `Windows Update Service`
  - Définis `Startup` sur `Automatic`
  - Clique sur `Start`
  - Clique sur `Ok`
  On va maintenant réessayer d’effectuer les mises à jour.
</details>

### Version minimum

Certains des outils qu’on doit installer sont compatibles avec la version `1903` **ou une version ultérieure** de Windows 10 ; on doit donc vérifier que tu as bien cette version au minimum.

- Appuie sur `Windows` + `R`
- Saisis `winver`
- Appuie sur `Enter`

Vérifie le **numéro de version** :

:heavy_check_mark: Si la version indique au moins `1903`, c’est bon :+1:

:x: S’il s’agit d’une version antérieure, **demande au prof**.


## Virtualisation

On doit vérifier que les options de virtualisation sont activées dans le BIOS de ton ordinateur.

C’est déjà le cas sur de nombreux ordinateurs. Vérifions-le :
- Appuie sur `Windows` + `R`
- Saisis `taskmgr`
- Appuie sur `Enter`
- Clique sur l’onglet `Performance`
- Clique sur `CPU`

![Gestionnaire des tâches de Windows](images/windows_task_manager.png)

:heavy_check_mark: Si tu vois « Virtualisation : activée », c’est bon :+1:

:x: Si la ligne est manquante ou si la virtualisation est désactivée, **demande au prof avant d’essayer d’activer la virtualisation**

<details>
  <summary>Activer la virtualisation</summary>

  On a besoin d’accéder au BIOS / à l’UEFI de l’ordinateur pour activer la virtualisation.

  - Appuie sur `Windows + R`
  - Saisis `shutdown.exe /r /o /t 1`
  - Appuie sur `Enter`
  - Attends que l’ordinateur s’arrête
  - Clique sur `Troubleshoot`
  - Clique sur `Advanced Options`
  - Clique sur `UEFI Firmware Settings`
  - Clique sur `Restart`

  Tu dois activer l’option de virtualisation de ton processeur ici :
  - La plupart du temps, dans les paramètres avancés, les paramètres du processeur ou les paramètres Northbridge
  - L’option peut avoir un nom différent en fonction de ton ordinateur :
    - Intel : `Intel VT-x`, `Intel Virtualization Technology`, `Virtualization Extensions`, `Vanderpool`...
    - AMD : `SVM Mode` ou `AMD-V`
  - Enregistre les modifications après activation et redémarre l’ordinateur en utilisant l’option correspondante
</details>


## Sous-système Windows pour Linux (WSL)

WSL est l’environnement de développement que l’on utilise pour exécuter Ubuntu. Pour en savoir plus sur WSL, [consulte cette page](https://docs.microsoft.com/fr-fr/windows/wsl/faq).

:information_source: Les instructions suivantes dépendent de ta version de Windows. Exécute uniquement les instructions qui correspondent à ta version :point_down:

### Windows 11

Si tu as Windows 11, nous allons installer WSL 2 et Ubuntu en une seule commande via le Windows Terminal.

:warning: Dans les instructions suivantes, utilise la combinaison de touches `Ctrl` + `Shift` + `Enter` pour exécuter **Windows Terminal** en tant qu’administrateur au lieu de cliquer simplement sur `Ok` ou d’appuyer sur `Enter`.

- Appuie sur `Windows` + `R`
- Saisis `wt`
- Appuie sur **`Ctrl` + `Shift` + `Enter`**

:warning: Tu devras peut-être accepter la confirmation UAC concernant l’octroi des droits d’administrateur.

Une fenêtre de terminal bleue apparaîtra :
- Copie la commande suivante (`Ctrl` + `C`)
- Colle-la dans la fenêtre du terminal (`Ctrl` + `V` ou en faisant un clic droit dans la fenêtre)
- Exécute-les en appuyant sur `Enter`

```powershell
wsl --install
```

:heavy_check_mark: Si la commande s’exécute sans erreur, redémarre ton ordinateur et suis les instructions ci-dessous :+1:

:x: Si tu obtiens un message d’erreur (ou si tu vois apparaître du texte en rouge dans la fenêtre), **demande au prof**

### Windows 10

#### Installer WSL 1

Si tu as Windows 10, on va d'abord installer WSL 1 à partir du terminal PowerShell.

:warning: Dans les instructions suivantes, utilise la combinaison de touches `Ctrl` + `Shift` + `Enter` pour exécuter **Windows PowerShell** en tant qu’administrateur au lieu de cliquer simplement sur `Ok` ou d’appuyer sur `Enter`.

- Appuie sur `Windows` + `R`
- Saisis `powershell`
- Appuie sur **`Ctrl` + `Shift` + `Enter`**

:warning: Tu devras peut-être accepter la confirmation UAC concernant l’octroi des droits d’administrateur.

Une fenêtre de terminal bleue apparaîtra :
- Copie les commandes suivantes une par une (`Ctrl` + `C`)
- Colle-les dans la fenêtre PowerShell (`Ctrl` + `V` ou en faisant un clic droit dans la fenêtre)
- Exécute-les en appuyant sur `Enter`

```powershell
Enable-WindowsOptionalFeature -Online -FeatureName Microsoft-Windows-Subsystem-Linux
```

```powershell
dism.exe /online /enable-feature /featurename:Microsoft-Windows-Subsystem-Linux /all /norestart
```

```powershell
dism.exe /online /enable-feature /featurename:VirtualMachinePlatform /all /norestart
```

:heavy_check_mark: Si les trois commandes s’exécutent sans erreur, redémarre ton ordinateur et suis les instructions ci-dessous :+1:

:x: Si tu obtiens un message d’erreur (ou si tu vois apparaître du texte en rouge dans la fenêtre), **demande au prof**

#### Mise à niveau vers WSL 2

Si tu as Windows 10, on va maintenant mettre à jour WSL à la version 2.

Une fois que ton ordinateur a redémarré, on doit télécharger le programme d’installation de WSL 2.

- Va sur la [page de téléchargement](https://aka.ms/wsl2kernel)
- Télécharge le « WSL2 Linux kernel update package 2 »
- Ouvre le fichier que tu viens de télécharger
- Clique sur `Suivant`
- Clique sur `Terminer`

![Mettre à jour WSL de la version 1 à 2](images/windows_update_wsl.png)

:heavy_check_mark: Si tu ne rencontres aucun message d’erreur, c’est bon :+1:

:x: Si tu obtiens l’erreur « Cette mise à jour s’applique seulement aux machines avec le sous-système Windows pour Linux », **fais un clic droit** sur le programme et sélectionne `uninstall` ; tu devrais pouvoir l’installer normalement cette fois-ci.

#### Définir WSL 2 comme sous-système Windows pour Linux par défaut

Si tu as Windows 10, on va enfin définir la version 2 de WSL comme étant la version par défaut.

Maintenant que WLS 2 est installé, on va le définir comme version par défaut :
- Appuie sur `Windows` + `R`
- Saisis `cmd`
- Appuie sur `Enter`

Dans la fenêtre qui apparaît, saisis :

```bash
wsl --set-default-version 2
```

:heavy_check_mark: Si tu vois apparaître « The operation completed successfully », tu peux fermer ce terminal et suivre les instructions ci-dessous :+1:

:x: Si le message qui s’affiche concerne la virtualisation, **demande au prof**

<details>
 <summary>Activer la fonction Virtual Machine Platform sous Windows</summary>

  Suis les étapes décrites [ici](https://www.configserverfirewall.com/windows-10/please-enable-the-virtual-machine-platform-windows-feature-and-ensure-virtualization-is-enabled-in-the-bios/#:~:text=To%20enable%20WSL%202,%20Open,Windows%20feature%20on%20or%20off.&text=Ensure%20that%20the%20Virtual%20Machine,Windows%20will%20enable%20WSL%202) pour activer <strong>Virtual Machine Platform</strong> et <strong>le sous-système Windows pour Linux</strong>
</details>

<details>
 <summary>Activer la fonction Hyper-V sous Windows</summary>

  Suis les étapes décrites [ici](https://winaero.com/enable-use-hyper-v-windows-10/) pour activer le groupe <strong>Hyper-V</strong>

  :information_source: Si tu as Windows 10 **Home edition**, la fonction Hyper-V n'est pas disponible sur ton système d'exploitation. Ce n'est pas bloquant et tu peux continuer à suivre les instructions ci-dessous :ok_hand:
</details>


## Ubuntu

### Installation

:information_source: Les instructions suivantes dépendent de ta version de Windows. N'exécute que les instructions qui correspondent à ta version :point_down:

#### Windows 11

Si tu as Windows 11, après avoir redémarré ton ordinateur, tu devrais voir une fenêtre de terminal indiquant que WSL poursuit le processus d'installation d'Ubuntu. Lorsque c'est terminé, Ubuntu va se lancer.

#### Windows 10

Si tu as Windows 10, installons Ubuntu via le Microsoft Store :

- Clique sur `Start`
- Saisis `Microsoft Store`
- Clique sur `Microsoft Store` dans la liste
- Recherche `Ubuntu` dans la barre de recherche
- **Sélectionne la version nommée « Ubuntu » sans aucun chiffre**
- Clique sur `Installer`

:warning: N’installe pas **Ubuntu 18.04 LTS** ni **Ubuntu 20.04** !

<details>
 <summary>Désinstaller les mauvaises versions d’Ubuntu</summary>

  Pour désinstaller une mauvaise version d’Ubuntu, il te suffit d’aller dans la liste des programmes installés de Windows 10 :
  - Appuie sur `Windows` + `R`
  - Saisis `ms-settings:appsfeatures`
  - Appuie sur `Enter`

  Trouve le logiciel à désinstaller et clique sur le bouton de désinstallation.
</details>

Une fois l’installation terminée, le bouton « Installer » se transforme en bouton « Lancer » ; clique dessus.

### Premier lancement

Au premier lancement, on te demandera de fournir des informations :
- Choisis un **nom d’utilisateur** :
  - un mot
  - en minuscules
  - sans caractères spéciaux
  - par exemple : `lewagon` ou ton `prenom`
- Choisis un **mot de passe**
- Confirme ton mot de passe

:warning: Lorsque tu saisiras ton mot de passe, rien ne s’affichera à l’écran ; **c’est normal**. Il s’agit d’une mesure de sécurité permettant de masquer ton mot de passe et sa longueur. Saisis simplement ton mot de passe, puis appuie sur `Enter`.

Tu peux fermer la fenêtre Ubuntu maintenant qu’elle est installée sur ton ordinateur.

### Vérifier la version de WSL sous Ubuntu

- Appuie sur `Windows` + `R`
- Saisis `cmd`
- Appuie sur `Enter`

Saisis la commande suivante :

```bash
wsl -l -v
```

:heavy_check_mark: Si la version de WSL sous Ubuntu est la 2, c’est bon. :+1:

:x: Si la version de WSL sous Ubuntu est la 1, il va falloir passer à la version 2.

<details>
  <summary>Passer de la version 1 à la version 2 de WSL sous Ubuntu</summary>

  Dans la fenêtre d’invite de commande, saisis :

  ```bash
  wsl --set-version Ubuntu 2
  ```

  :heavy_check_mark: Au bout de quelques secondes, tu devrais voir apparaître le message suivant : `The conversion is complete`.

  :x: Si ce n’est pas le cas, il faut vérifier que les fichiers Ubuntu ne sont pas compressés.
</details>

<details>
  <summary>Vérifier que les fichiers sont décompressés</summary>

  - Appuie sur `Windows` + `R`
  - Saisis `%localappdata%\Packages`
  - Appuie sur `Enter`
  - Ouvre le dossier nommé `CanonicalGroupLimited.UbuntuonWindows...`
  - Fais un clic droit sur le dossier `LocalState`
  - Clique sur `Properties`
  - Clique sur `Advanced`
  - Vérifie que l’option `Compresser le contenu` n’est **pas** cochée, puis clique sur `Ok`.

  Applique les modifications à ce dossier uniquement et réessaie de convertir la version de WSL sous Ubuntu.

  :x: Si la conversion ne fonctionne pas, **demande au prof**.
</details>

Tu peux maintenant fermer cette fenêtre de terminal.
