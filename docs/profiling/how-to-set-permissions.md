---
title: Définir les autorisations | Microsoft Docs
description: Découvrez comment un administrateur d’un ordinateur accorde les autorisations de sécurité requises pour le profilage à un utilisateur ou un groupe qui ne dispose pas d’autorisations d’administrateur.
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- profiling, setting permissions
- security [Visual Studio ALM], setting permissions
- permissions [Visual Studio ALM], profiling
- profiling tools, setting profiling permissions
- performance tools, setting profiling permissions
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 2ab51b317164b8f2e828e0327021fb595574583c
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2021
ms.locfileid: "98721994"
---
# <a name="how-to-set-permissions"></a>Guide pratique pour définir les autorisations

Cet article explique comment l’administrateur d’un ordinateur accorde les autorisations de sécurité requises pour le profilage à un utilisateur ou à un groupe qui ne dispose pas des autorisations d’administrateur sur cet ordinateur.

Selon un principe de sécurité de base, les applications ne doivent pas s’exécuter avec plus d’autorisations que nécessaire. Ce principe s’applique également aux utilisateurs. Si les utilisateurs peuvent travailler de manière pleinement efficace quand ils se connectent en tant que membres du groupe Utilisateurs et non du groupe Administrateurs, ils ne doivent pas bénéficier d’autorisations d’administrateur. La première procédure, « Pour créer un compte d’utilisateur disposant d’autorisations utilisateurs », explique comment créer un compte d’utilisateur pour un membre du groupe Utilisateurs.

Les membres du groupe Utilisateurs devront pouvoir accéder aux dossiers et fichiers du disque qui sont partagés avec les autres membres de l’équipe. La deuxième procédure, « Pour accorder l’accès aux fichiers projet partagés », explique comment accorder cet accès.

Les membres du groupe Utilisateurs peuvent exécuter les outils de profilage si un administrateur leur accorde l’accès au pilote logiciel pour les outils de profilage. La dernière procédure, « Pour accorder l’accès au pilote de profilage », explique comment accorder l’accès à ce pilote.

> [!NOTE]
> Pour suivre les étapes de ces procédures, vous devez disposer d’autorisations d’administrateur.

## <a name="to-create-a-user-account-that-has-user-permissions"></a>Pour créer un compte d’utilisateur disposant d’autorisations utilisateurs

1. Cliquez avec le bouton droit sur **poste de travail** , puis cliquez sur **gérer**.

     La fenêtre **Gestion de l’ordinateur** s’ouvre.

2. Développez **Utilisateurs et groupes locaux**.

3. Cliquez avec le bouton droit sur le dossier **Utilisateurs**, puis cliquez sur **Nouvel utilisateur**.

     La boîte de dialogue **Nouvel utilisateur** s’affiche.

4. Renseignez les champs de cette boîte de dialogue avec les informations du compte d’utilisateur que vous créez. Permet de spécifier un mot de passe. Cochez éventuellement la case qui exige que l’utilisateur modifie le mot de passe à la prochaine connexion.

5. Cliquez sur **créer** , puis sur **Fermer**.

     Le nouvel utilisateur apparaît dans le groupe Utilisateurs, un groupe d’utilisateurs qui ne disposent pas d’autorisations d’administrateur.

## <a name="to-grant-access-to-shared-project-files"></a>Pour accorder l’accès aux fichiers projet partagés

1. Dans l’Explorateur Windows (ou l’Explorateur de fichiers), localisez la racine de l’arborescence de dossiers pour accéder aux fichiers projet utilisés par cet utilisateur et partagés par l’équipe du projet.

     Le chemin de ce dossier peut se présenter comme suit :

    ```cmd
    D:\ourProject
    ```

2. Cliquez avec le bouton droit sur le dossier, puis cliquez sur **Propriétés**.

     La boîte de dialogue **\<folder name> Propriétés** s’affiche.

3. Cliquez sur l’onglet **Security** .

4. Cliquez sur le nom du compte de l’utilisateur dans la zone **Noms de groupes ou d’utilisateurs**.

5. Dans la zone **autorisations \<user name> pour** , activez la case à cocher **contrôle total**.

6. Cliquez sur **OK**.

     Cette procédure accorde à l’utilisateur les autorisations pour l’arborescence de dossiers partagés qui commence par le dossier sélectionné à l’étape 5.

## <a name="to-grant-access-to-the-profiling-driver"></a>Pour accorder l’accès au pilote de profilage

1. Ouvrez une invite de commandes en tant qu’administrateur.

2. Remplacez le répertoire par :

    ```cmd
    <drive>:\Program Files\Microsoft Visual Studio 14\Team Tools\Performance Tools
    ```

3. Exécutez la commande suivante :

    ```cmd
    vsperfcmd /admin:driver,start /admin:service,start
    ```

     Cette commande installe et démarre le pilote des outils de profilage.

     Cette commande démarre le pilote et le service de profilage afin que les utilisateurs non-administrateurs puissent utiliser les fonctionnalités de profilage disponibles dans leur espace de processus utilisateur. Seul un administrateur peut exécuter cette commande. Elle ne s’exécutera pas pour les utilisateurs non-administrateurs.

     Notez que les effets de cette étape sont annulés après le redémarrage de l’ordinateur, sauf si vous exécutez également la dernière étape de cette procédure.

4. Exécutez la commande pour autoriser l’accès aux fonctionnalités du pilote de profilage par un utilisateur ou un groupe ne disposant pas de l’accès administrateur à l’ordinateur :

    ```cmd
    vsperfcmd /admin:security,allow,<right[,right],<user name|group name>
    ```

     Cette commande accorde au \<user name> compte ou l' \<group name> accès aux outils de profilage. L' \<right> option détermine les fonctionnalités de profilage auxquelles l’utilisateur peut accéder. L' \<right> option peut être une ou plusieurs des valeurs suivantes :

    - FullAccess : autorise l’accès à toutes les méthodes de profilage, notamment la collecte des données de performance à partir des services, l’échantillonnage et le profilage intersession.

    - SampleProfiling : autorise l’accès aux méthodes de profilage d’échantillon.

    - CrossSession : autorise l’accès au profilage intersession exigé pour les services de profilage.

5. (Facultatif) Pour conserver les résultats de l’une des étapes précédentes après le redémarrage de l’ordinateur, exécutez la commande suivante :

    ```cmd
    vsperfcmd /admin:driver,autostart,on
    ```

   Après s’être connectés, les utilisateurs spécifiés pourront désormais utiliser les outils de profilage sans disposer d’autorisations d’administrateur.

## <a name="see-also"></a>Voir aussi

[Configurer des sessions](../profiling/configuring-performance-sessions.md) 
 de performance [VSPerfCmd](../profiling/vsperfcmd.md) 
 [Profilage et sécurité Windows Vista](../profiling/profiling-and-windows-vista-security.md)
