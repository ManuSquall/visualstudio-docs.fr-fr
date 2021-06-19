---
title: Déploiement MSI et VSIX d'un langage spécifique à un domaine
description: Découvrez comment vous pouvez installer un langage spécifique à un domaine (DSL) sur votre propre ordinateur ou sur d’autres ordinateurs.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 879028746eac10160492f03651ef8b51714e9c6a
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112391008"
---
# <a name="msi-and-vsix-deployment-of-a-dsl"></a>Déploiement MSI et VSIX d'un langage spécifique à un domaine
Vous pouvez installer un langage spécifique à un domaine sur votre ordinateur ou sur d’autres ordinateurs. Visual Studio doit déjà être installé sur l’ordinateur cible.

## <a name="choosing-between-vsix-and-msi-deployment"></a><a name="which"></a> Choix entre un déploiement VSIX et un déploiement MSI
 Il existe deux méthodes de déploiement d’un langage spécifique à un domaine :

|Méthode|Avantages|
|-|-|
|VSX (extension Visual Studio)|Très facile à déployer : copiez et exécutez le fichier **. vsix** à partir du projet DslPackage.<br /><br /> Pour plus d’informations [, consultez Installation et désinstallation d’une solution DSL à l’aide de VSX](#Installing).|
|MSI (fichier du programme d’installation)|-Permet à l’utilisateur d’ouvrir Visual Studio en double-cliquant sur un fichier DSL.<br />-Associe une icône au type de fichier DSL sur l’ordinateur cible.<br />-Associe un XSD (schéma XML) au type de fichier DSL. Cela évite les avertissements lorsque le fichier est chargé dans Visual Studio.<br /><br /> Vous devez ajouter un projet d’installation à votre solution pour créer un MSI.<br /><br /> Pour plus d’informations, consultez [déploiement d’une solution DSL à l’aide d’un fichier MSI](#msi).|

## <a name="install-and-uninstall-a-dsl-by-using-the-vsx"></a><a name="Installing"></a> Installer et désinstaller un DSL à l’aide de VSX

Lorsque votre solution DSL est installée par cette méthode, l’utilisateur peut ouvrir un fichier DSL à partir de Visual Studio, mais ce fichier ne peut pas être ouvert à partir de l’Explorateur Windows.

### <a name="to-install-a-dsl-by-using-the-vsx"></a>Pour installer une solution DSL à l’aide de la VSX

1. Recherchez le fichier **. vsix** généré par votre projet de package DSL :

   1. Dans **Explorateur de solutions**, cliquez avec le bouton droit sur le projet **DslPackage** , puis cliquez sur **ouvrir le dossier dans l’Explorateur de fichiers**.

   2. Localisez le **fichier \\ \* \\ bin**_YourProject_**. DslPackage. vsix**

2. Copiez le fichier **. vsix** sur l’ordinateur cible sur lequel vous souhaitez installer le DSL. Il peut s’agir de votre propre ordinateur ou d’un autre.

   - L’ordinateur cible doit avoir l’une des éditions de [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] qui prend en charge DSL au moment de l’exécution. Pour plus d’informations, consultez [éditions de Visual Studio prises en charge pour la visualisation & le kit de développement logiciel Modeling SDK](../modeling/supported-visual-studio-editions-for-visualization-amp-modeling-sdk.md).

   - L’une des éditions de Visual Studio doit être spécifiée dans **DslPackage\source.extensions.manifest** pour l’ordinateur cible.

3. Sur l’ordinateur cible, double-cliquez sur le fichier **. vsix** .

    Le **Programme d’installation des extensions Visual Studio** s’ouvre et installe l’extension.

4. Démarrez ou redémarrez [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)].

5. Pour tester le DSL, utilisez Visual Studio pour créer un nouveau fichier qui a l’extension que vous avez définie pour votre DSL.

### <a name="to-uninstall-a-dsl-that-was-installed-by-using-vsx"></a>Pour désinstaller un DSL qui a été installé à l’aide de VSX

1. Dans le menu **Outils** , choisissez **Extensions et mises à jour**.

2. Développez **Extensions installées**.

3. Sélectionnez l’extension dans laquelle la DSL est définie, puis cliquez sur **désinstaller**.

   Exceptionnellement, une extension défaillante ne parvient pas à se charger et crée un rapport dans la fenêtre d’erreur, mais ne s’affiche pas dans le Gestionnaire d’extensions. Dans ce cas, vous pouvez supprimer l’extension en supprimant le fichier de l’emplacement suivant :

   *LocalAppData* **\Microsoft\VisualStudio\10.0\Extensions**

## <a name="deploying-a-dsl-in-an-msi"></a><a name="msi"></a> Déploiement d’une solution DSL dans un MSI
 En définissant un fichier MSI (Windows Installer) pour votre DSL, vous pouvez autoriser les utilisateurs à ouvrir des fichiers DSL à partir de l’Explorateur Windows. Vous pouvez également associer une icône et une brève description à votre extension de nom de fichier. En outre, le MSI peut installer un XSD qui peut être utilisé pour valider des fichiers DSL. Si vous le souhaitez, vous pouvez ajouter d’autres composants à la MSI qui seront installés en même temps.

 Pour plus d’informations sur les fichiers MSI et d’autres options de déploiement, consultez [déploiement d’applications, de services et de composants](../deployment/deploying-applications-services-and-components.md).

 Pour générer un MSI, vous devez ajouter un projet d’installation à votre solution Visual Studio. La méthode la plus simple pour créer un projet d’installation consiste à utiliser le modèle CreateMsiSetupProject.tt, que vous pouvez télécharger à partir du [site VMSDK](https://code.msdn.microsoft.com/Visualization-and-Modeling-313535db).

### <a name="to-deploy-a-dsl-in-an-msi"></a>Pour déployer un DSL dans un MSI

1. Défini `InstalledByMsi` dans le manifeste de l’extension. Cela empêche l’installation et la désinstallation de la VSX, sauf par le MSI. Cela est important si vous incluez d’autres composants dans le MSI.

   1. Ouvrir DslPackage\source.extension.tt

   2. Insérez la ligne suivante avant `<SupportedProducts>` :

       ```xml
       <InstalledByMsi>true</InstalledByMsi>
       ```

2. Créez ou modifiez une icône qui représente votre DSL dans l’Explorateur Windows. Par exemple, modifiez **DslPackage\Resources\File.ico**

3. Assurez-vous que les attributs suivants de votre DSL sont corrects :

   - Dans l’Explorateur DSL, cliquez sur le nœud racine et, dans Fenêtre Propriétés, consultez :

       - Description

       - Version

   - Cliquez sur le nœud **éditeur** et dans le fenêtre Propriétés, cliquez sur l' **icône**. Définir la valeur pour référencer un fichier d’icône dans **DslPackage\Resources**, tel que **file. ico**

   - Dans le menu **générer** , ouvrez **Configuration Manager**, puis sélectionnez la configuration que vous souhaitez générer, par exemple **version finale** ou **débogage**.

4. Accédez à la [page d’hébergement du kit de développement logiciel de visualisation et de modélisation](https://code.msdn.microsoft.com/Visualization-and-Modeling-313535db), puis, sous l’onglet **téléchargements** , téléchargez **CreateMsiSetupProject.TT**.

5. Ajoutez **CreateMsiSetupProject.TT** à votre projet DSL.

    Visual Studio crée un fichier nommé **CreateMsiSetupProject. vdproj**.

6. Dans l’Explorateur Windows, copiez DSL \\ *. vdproj vers un nouveau dossier nommé Setup.

    (Si vous le souhaitez, vous pouvez maintenant exclure CreateMsiSetupProject.tt de votre projet DSL.)

7. Dans **Explorateur de solutions**, ajoutez **Setup \\ \* . vdproj** en tant que projet existant.

8. Dans le menu **projet** , cliquez sur **dépendances du projet**.

    Dans la boîte de dialogue **dépendances du projet** , sélectionnez le projet d’installation.

    Activez la case à cocher en regard de **DslPackage**.

9. Régénérez la solution.

10. Dans l’Explorateur Windows, localisez le fichier MSI généré dans votre projet d’installation.

     Copiez le fichier MSI sur un ordinateur sur lequel vous souhaitez installer votre DSL. Double-cliquez sur le fichier MSI. Le programme d'installation s'exécute.

11. Sur l’ordinateur cible, créez un nouveau fichier qui a l’extension de fichier de votre DSL. Vérifiez que :

    - Dans le mode liste de l’Explorateur Windows, le fichier apparaît avec l’icône et la description que vous avez définies.

    - Lorsque vous double-cliquez sur le fichier, Visual Studio démarre et ouvre le fichier DSL dans votre éditeur DSL.

    Si vous préférez, vous pouvez créer le projet d’installation manuellement, au lieu d’utiliser le modèle de texte. Pour obtenir une procédure pas à pas qui comprend cette procédure, consultez le chapitre 5 du [laboratoire de visualisation et de modélisation SDK](https://code.msdn.microsoft.com/DSLToolsLab/Release/ProjectReleases.aspx?ReleaseId=4207).

### <a name="to-uninstall-a-dsl-that-was-installed-from-an-msi"></a>Pour désinstaller un DSL qui a été installé à partir d’un MSI

1. Dans Windows, ouvrez le panneau de configuration **programmes et fonctionnalités** .

2. Désinstallez le DSL.

3. Démarrez Visual Studio.
