---
title: Déploiement MSI et VSIX d'un langage spécifique à un domaine
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 2f5b8948d94c64d84b33714a4b432a46bfb73b59
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49931543"
---
# <a name="msi-and-vsix-deployment-of-a-dsl"></a>Déploiement MSI et VSIX d'un langage spécifique à un domaine
Vous pouvez installer une langue spécifique à un domaine sur votre ordinateur ou sur d’autres ordinateurs. Visual Studio doit déjà être installé sur l’ordinateur cible.

## <a name="which"></a> Choix entre VSIX et de déploiement MSI
 Il existe deux méthodes de déploiement d’un langage spécifique à un domaine :

|Méthode|Avantages|
|-|-|
|VSX (Extension de Visual Studio)|Très facile à déployer : copie et d’exécuter le **.vsix** fichier à partir du projet DslPackage.<br /><br /> Pour plus d’informations, consultez [installation et désinstallation d’une solution DSL à l’aide de la VSX](#Installing).|
|MSI (fichier de programme d’installation)|-Permet à l’utilisateur ouvrir Visual Studio en double-cliquant sur un fichier DSL.<br />-Associe une icône avec le type de fichier DSL dans l’ordinateur cible.<br />-Associe un XSD (schéma XML) avec le type de fichier DSL. Cela évite des avertissements lorsque le fichier est chargé dans Visual Studio.<br /><br /> Vous devez ajouter un projet d’installation à votre solution pour créer un fichier MSI.<br /><br /> Pour plus d’informations, consultez [déploiement d’une solution DSL à l’aide d’un fichier MSI](#msi).|

## <a name="Installing"></a> Installation et désinstallation d’une solution DSL à l’aide de la VSX
 Lorsque votre solution DSL est installé par cette méthode, l’utilisateur peut ouvrir un fichier DSL à partir de Visual Studio, mais le fichier ne peut pas être ouvert à partir de l’Explorateur Windows.

#### <a name="to-install-a-dsl-by-using-the-vsx"></a>Pour installer une solution DSL à l’aide de la VSX

1. Sur votre ordinateur, recherchez le **.vsix** fichier qui a été généré par votre projet de Package DSL.

   1.  Dans **l’Explorateur de solutions**, avec le bouton droit le **DslPackage** de projet, puis cliquez sur **ouvrir le dossier dans l’Explorateur Windows**.

   2.  Recherchez le fichier **bin\\\*\\**_VotreProjet_**. DslPackage.vsix**

2. Copie le **.vsix** fichier sur l’ordinateur cible sur lequel vous souhaitez installer la solution DSL. Il peut s’agir de votre propre ordinateur ou d’un autre.

   - L’ordinateur cible doit avoir une des éditions de [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] qui prend en charge les langages DSL en cours d’exécution. Pour plus d’informations, consultez [pris en charge les éditions Visual Studio pour Visualization and Modeling SDK](../modeling/supported-visual-studio-editions-for-visualization-amp-modeling-sdk.md).

   - L’ordinateur cible doit avoir une des éditions de Visual Studio spécifié dans **DslPackage\source.extensions.manifest**.

3. Sur l’ordinateur cible, double-cliquez sur le **.vsix** fichier.

    Le**Programme d’installation des extensions Visual Studio** s’ouvre et installe l’extension.

4. Démarrez ou redémarrez [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)].

5. Pour tester la solution DSL, utilisez Visual Studio pour créer un nouveau fichier portant l’extension que vous avez défini pour votre DSL.

#### <a name="to-uninstall-a-dsl-that-was-installed-by-using-vsx"></a>Pour désinstaller une solution DSL a été installée à l’aide de VSX

1. Sur le **outils** menu, cliquez sur **Gestionnaire d’extensions**.

2. Développez **Extensions installées**.

3. Sélectionnez l’extension dans lequel la solution DSL est défini, puis cliquez sur **désinstallation**.

   Exceptionnellement, une extension défaillante ne parvient pas à se charger et crée un rapport dans la fenêtre d’erreur, mais ne s’affiche pas dans le Gestionnaire d’extensions. Dans ce cas, vous pouvez supprimer l’extension en supprimant le fichier de l’emplacement suivant :

   *LocalAppData* **\Microsoft\VisualStudio\10.0\Extensions**

## <a name="msi"></a> Déploiement d’une solution DSL dans un fichier MSI
 En définissant un fichier MSI (Windows Installer) pour votre DSL, vous pouvez autoriser les utilisateurs à ouvrir des fichiers DSL à partir de l’Explorateur Windows. Vous pouvez également associer une icône et une brève description votre extension de nom de fichier. En outre, le fichier MSI peut installer un XSD qui peut être utilisé pour valider des fichiers DSL. Si vous le souhaitez, vous pouvez ajouter d’autres composants dans le fichier MSI qui est installé en même temps.

 Pour plus d’informations sur les fichiers MSI et d’autres options de déploiement, consultez [déploiement d’Applications, Services et composants](../deployment/deploying-applications-services-and-components.md).

 Pour générer un fichier MSI, vous ajoutez un projet d’installation à votre solution Visual Studio. La méthode la plus simple de création d’un projet d’installation consiste à utiliser le modèle CreateMsiSetupProject.tt, que vous pouvez télécharger depuis le [site VMSDK](http://go.microsoft.com/fwlink/?LinkID=186128).

#### <a name="to-deploy-a-dsl-in-an-msi"></a>Pour déployer une solution DSL dans un fichier MSI

1. Définissez `InstalledByMsi` dans le manifeste d’extension. Cela empêche le VSX installé et désinstallé à l’exception par le fichier MSI. Ceci est important si vous inclurez des autres composants dans le fichier MSI.

   1.  Ouvrez DslPackage\source.extension.tt

   2.  Insérez la ligne suivante avant `<SupportedProducts>`:

       ```xml
       <InstalledByMsi>true</InstalledByMsi>
       ```

2. Créez ou modifiez une icône qui représentera votre DSL dans l’Explorateur Windows. Par exemple, modifiez **DslPackage\Resources\File.ico**

3. Assurez-vous que les attributs suivants de votre DSL sont corrects :

   -   Cliquez sur le nœud racine dans l’Explorateur DSL et dans la fenêtre Propriétés, consultez :

       -   Description

       -   Version

   -   Cliquez sur le **éditeur** nœud dans la fenêtre Propriétés, cliquez sur **icône**. Définissez la valeur pour référencer un fichier d’icône **DslPackage\Resources**, tel que **File.ico**

   -   Sur le **Build** menu, ouvrez **Configuration Manager**et sélectionnez la configuration que vous souhaitez générer, tel que **version** ou **déboguer** .

4. Accédez à [page d’accueil Visualization and Modeling SDK](http://go.microsoft.com/fwlink/?LinkID=186128)et à partir de la **télécharge** onglet, téléchargez **CreateMsiSetupProject.tt**.

5. Ajouter **CreateMsiSetupProject.tt** à votre projet Dsl.

    Visual Studio crée un fichier nommé **CreateMsiSetupProject.vdproj**.

6. Dans l’Explorateur Windows, copiez Dsl\\\*.vdproj vers un nouveau dossier nommé le programme d’installation.

    (Si vous le souhaitez, vous pouvez désormais exclure CreateMsiSetupProject.tt à partir de votre projet Dsl.)

7. Dans **l’Explorateur de solutions**, ajouter **le programme d’installation\\\*.vdproj** qu’un projet existant.

8. Sur le **projet** menu, cliquez sur **dépendances du projet**.

    Dans le **dépendances du projet** boîte de dialogue, sélectionnez le projet d’installation.

    Activez la case en regard **DslPackage**.

9. Régénérez la solution.

10. Dans l’Explorateur Windows, localisez le fichier MSI généré dans votre projet d’installation.

     Copiez le fichier MSI sur un ordinateur sur lequel vous souhaitez installer votre DSL. Double-cliquez sur le fichier MSI. Le programme d’installation s’exécute.

11. Dans l’ordinateur cible, créez un nouveau fichier qui porte l’extension de fichier de votre DSL. Vérifiez que :

    -   Dans la vue de liste de l’Explorateur Windows, le fichier s’affiche avec l’icône et la description que vous avez défini.

    -   Lorsque vous double-cliquez sur le fichier, Visual Studio démarre et ouvre le fichier DSL dans l’éditeur de votre DSL.

    Si vous préférez, vous pouvez créer le projet d’installation manuellement, au lieu d’utiliser le modèle de texte. Pour une procédure pas à pas qui inclut cette procédure, consultez le chapitre 5 du [de visualisation et modélisation de laboratoire de kit de développement logiciel](http://go.microsoft.com/fwlink/?LinkId=208878).

#### <a name="to-uninstall-a-dsl-that-was-installed-from-an-msi"></a>Pour désinstaller une solution DSL a été installée à partir d’un fichier MSI

1.  Dans Windows, ouvrez le **programmes et fonctionnalités** le panneau de configuration.

2.  Désinstaller la solution DSL.

3.  Redémarrez Visual Studio.