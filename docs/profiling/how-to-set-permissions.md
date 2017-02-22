---
title: "Comment&#160;: d&#233;finir des autorisations de profilage | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "profilage, définir des autorisations"
  - "sécurité [Visual Studio ALM], définir des autorisations"
  - "autorisations [Visual Studio ALM], profilage"
  - "outils de profilage, définir des autorisations de profilage"
  - "outils d’analyse des performances, définir des autorisations de profilage"
ms.assetid: 69f27896-8f46-4ef3-bfb7-726d95304f3a
caps.latest.revision: 23
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 23
---
# Comment&#160;: d&#233;finir des autorisations de profilage
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Cette rubrique explique comment l'administrateur d'un ordinateur accorde les autorisations de sécurité requises pour le profilage à un utilisateur ou un groupe qui ne dispose pas des autorisations Administrateur sur cet ordinateur.  
  
 Selon un principe de sécurité de base, les applications ne doivent pas s'exécuter avec plus d'autorisations qu'elles n'en ont besoin.  Ce principe s'applique également aux utilisateurs.  Ainsi, si les utilisateurs peuvent travailler de manière effective lorsqu'ils se connectent en tant que membres du groupe Utilisateurs et non du groupe Administrateurs, ils ne doivent pas bénéficier des autorisations Administrateur.  La première procédure, « Pour créer un compte d'utilisateur qui a des autorisations Utilisateurs », décrit comment créer un compte d'utilisateur pour un membre du groupe Utilisateurs.  
  
 **Conditions requises**  
  
-   [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)], [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)], [!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)]  
  
 Les membres du groupe Utilisateurs auront besoin d'accéder aux dossiers et aux fichiers du disque qui sont partagés avec les autres membres de l'équipe.  La deuxième procédure, « Pour accorder l'accès aux fichiers projet partagés », décrit comment accorder cet accès.  
  
 Les membres du groupe Utilisateurs peuvent exécuter les outils de profilage si un administrateur leur accorde l'accès au pilote de logiciel des outils de profilage.  La dernière procédure, « Pour accorder l'accès au pilote de profilage », décrit comment accorder l'accès à ce pilote.  
  
> [!NOTE]
>  Pour suivre les étapes de ces procédures, vous devez avoir des autorisations d'administrateur.  
  
### Pour créer un compte d'utilisateur qui a des autorisations Utilisateurs  
  
1.  Cliquez avec le bouton droit sur **Poste de travail** et cliquez sur **Gérer**.  
  
     La fenêtre **Gestion de l'ordinateur** s'ouvre.  
  
2.  Développez **Utilisateurs et groupes locaux**.  
  
3.  Cliquez avec le bouton droit sur le dossier **Utilisateurs**, puis cliquez sur **Nouvel utilisateur**.  
  
     La boîte de dialogue **Nouvel utilisateur** s'affiche.  
  
4.  Remplissez les champs de cette boîte de dialogue avec les informations du compte d'utilisateur que vous créez.  Spécifiez un mot de passe.  Sélectionnez éventuellement la case à cocher qui requiert que l'utilisateur modifie le mot de passe à la prochaine connexion.  
  
5.  Cliquez sur **Créer**, puis sur **Fermer**.  
  
     Le nouvel utilisateur apparaît dans le groupe Utilisateurs, un groupe d'utilisateurs qui n'a pas d'autorisations Administrateur.  
  
### Pour accorder l'accès aux fichiers projet partagés  
  
1.  Dans l'Explorateur Windows \(ou l'explorateur de fichier\), recherchez la racine de l'arborescence du dossier pour les fichiers de type projet utilisés par cet utilisateur et partagés par l'équipe du projet.  
  
     Le chemin d'accès de ce dossier peut se présenter comme suit :  
  
    ```  
    D:\ourProject  
    ```  
  
2.  Cliquez avec le bouton droit sur le dossier, puis cliquez sur **Propriétés**.  
  
     La boîte de dialogue **Propriétés de\<nom du dossier\>** s'affiche.  
  
3.  Cliquez sur l'onglet **Sécurité**.  
  
4.  Cliquez sur le nom du compte de l'utilisateur dans la zone **Noms d'utilisateurs ou de groupes**.  
  
5.  Dans la zone **Autorisations pour \<NomUtilisateur\>**, activez la case à cocher correspondant à **Contrôle total**.  
  
6.  Cliquez sur **OK**.  
  
     Cette action accorde les autorisations à l'utilisateur pour l'arborescence de dossier partagé qui commence par le dossier sélectionné à l'étape 5.  
  
### Pour accorder l'accès au pilote de profilage  
  
1.  Ouvrez une invite de commandes en tant qu'administrateur.  
  
2.  Remplacez le répertoire par :  
  
    ```  
    <drive>:\Program Files\Microsoft Visual Studio 10\Team Tools\Performance Tools  
    ```  
  
3.  Exécutez la commande suivante :  
  
    ```  
    vsperfcmd /admin:driver,start /admin:service,start  
    ```  
  
     Cette commande installe et démarre le pilote des outils de profilage.  
  
     Cette commande démarre le pilote et le service de profilage afin que les utilisateurs non\-administrateurs puissent utiliser les fonctionnalités de profilage disponibles dans leur espace de processus utilisateur.  Seul un administrateur peut exécuter cette commande ; elle ne s'exécutera pas pour les utilisateurs non administrateurs.  
  
     Notez que les effets de cette étape sont annulés après le redémarrage de l'ordinateur, à moins que vous n'exécutiez également la dernière étape de cette procédure.  
  
4.  Exécutez la commande pour autoriser l'accès aux fonctionnalités du pilote de profilage à un utilisateur ou un groupe qui ne dispose pas de l'accès administrateur à l'ordinateur :  
  
    ```  
    vsperfcmd /admin:security,allow,<right[,right],<user name|group name>  
    ```  
  
     Cette commande accorde au compte \<user name\> \(nom d'utilisateur\) ou \<group name\> \(nom de groupe\) l'accès aux outils de profilage.  L'option \<right\> détermine les fonctionnalités de profilage accessibles à l'utilisateur.  L'option de \<droite\> peut avoir une ou plusieurs des valeurs suivantes :  
  
    -   FullAccess : autorise l'accès à toutes les méthodes de profilage, y compris la collecte des données de performance à partir des services, l'échantillonnage et le profilage intersession.  
  
    -   SampleProfiling : autorise l'accès aux méthodes de profilage par échantillonnage.  
  
    -   CrossSession : autorise l'accès au profilage intersession requis pour les services de profilage.  
  
5.  \(Facultatif\) Pour conserver les résultats de l'une des étapes précédentes après le redémarrage de l'ordinateur, exécutez la commande suivante :  
  
    ```  
    vsperfcmd /admin:driver,autostart,on  
    ```  
  
 Les utilisateurs spécifiés, après s'être connectés, pourront désormais utiliser les outils de profilage sans disposer d'autorisations Administrateur.  
  
## Voir aussi  
 [Configuration de sessions de performance](../profiling/configuring-performance-sessions.md)   
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profilage et sécurité Windows Vista](../profiling/profiling-and-windows-vista-security.md)