---
title: Déploiement MSI et VSIX d’un DSL | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: 6ce16f06-1978-4e19-8cdc-441ee65a3fb2
caps.latest.revision: 4
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 4917fc81f439ef0185a753fb1c4c85e460eb7681
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74297739"
---
# <a name="msi-and-vsix-deployment-of-a-dsl"></a>Déploiement MSI et VSIX d'un langage spécifique à un domaine
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous pouvez installer un langage spécifique à un domaine sur votre ordinateur ou sur d’autres ordinateurs. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] doit déjà être installé sur l’ordinateur cible.

## <a name="which"></a>Choix entre un déploiement VSIX et un déploiement MSI
 Il existe deux méthodes de déploiement d’un langage spécifique à un domaine :

|Méthode|Avantages|
|------------|--------------|
|VSX (extension de[!INCLUDE[vsprvs](../includes/vsprvs-md.md)])|Très facile à déployer : copiez et exécutez le fichier **. vsix** à partir du projet DslPackage.<br /><br /> Pour plus d’informations [, consultez Installation et désinstallation d’une solution DSL à l’aide de VSX](#Installing).|
|MSI (fichier du programme d’installation)|-Permet à l’utilisateur d’ouvrir [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] en double-cliquant sur un fichier DSL.<br />-Associe une icône au type de fichier DSL sur l’ordinateur cible.<br />-Associe un XSD (schéma XML) au type de fichier DSL. Cela évite les avertissements lorsque le fichier est chargé dans [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].<br /><br /> Vous devez ajouter un projet d’installation à votre solution pour créer un MSI.<br /><br /> Pour plus d’informations, consultez [déploiement d’une solution DSL à l’aide d’un fichier MSI](#msi).|

## <a name="Installing"></a>Installation et désinstallation d’une solution DSL à l’aide de la VSX
 Lorsque votre solution DSL est installée par cette méthode, l’utilisateur peut ouvrir un fichier DSL à partir de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], mais ce fichier ne peut pas être ouvert à partir de l’Explorateur Windows.

#### <a name="to-install-a-dsl-by-using-the-vsx"></a>Pour installer une solution DSL à l’aide de la VSX

1. Sur votre ordinateur, recherchez le fichier **. vsix** généré par votre projet de package DSL.

    1. Dans **Explorateur de solutions**, cliquez avec le bouton droit sur le projet **DslPackage** , puis cliquez sur **ouvrir le dossier dans l’Explorateur Windows**.

    2. Localisez le fichier **bin\\\*\\** _YourProject_ **. DslPackage. vsix**

2. Copiez le fichier **. vsix** sur l’ordinateur cible sur lequel vous souhaitez installer le DSL. Il peut s’agir de votre propre ordinateur ou d’un autre ordinateur.

    - L’ordinateur cible doit avoir l’une des éditions de [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] qui prend en charge DSL au moment de l’exécution. Pour plus d’informations, consultez [éditions de Visual Studio prises en charge pour la visualisation & le kit de développement logiciel Modeling SDK](../modeling/supported-visual-studio-editions-for-visualization-amp-modeling-sdk.md).

    - L’ordinateur cible doit avoir l’une des éditions de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] spécifiées dans **DslPackage\source.extensions.manifest**.

3. Sur l’ordinateur cible, double-cliquez sur le fichier **. vsix** .

     Le**Programme d’installation des extensions Visual Studio** s’ouvre et installe l’extension.

4. Démarrez ou redémarrez [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)].

5. Pour tester le DSL, utilisez [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] pour créer un nouveau fichier avec l’extension que vous avez définie pour votre DSL.

#### <a name="to-uninstall-a-dsl-that-was-installed-by-using-vsx"></a>Pour désinstaller un DSL qui a été installé à l’aide de VSX

1. Dans le menu **Outils** , cliquez sur **Gestionnaire d’extensions**.

2. Développez **Extensions installées**.

3. Sélectionnez l’extension dans laquelle la DSL est définie, puis cliquez sur **désinstaller**.

   Exceptionnellement, une extension défaillante ne parvient pas à se charger et crée un rapport dans la fenêtre d’erreur, mais ne s’affiche pas dans le Gestionnaire d’extensions. Dans ce cas, vous pouvez supprimer l’extension en supprimant le fichier de l’emplacement suivant :

   *LocalAppData* **\Microsoft\VisualStudio\10.0\Extensions**

## <a name="msi"></a>Déploiement d’une solution DSL dans un MSI
 En définissant un fichier MSI (Windows Installer) pour votre DSL, vous pouvez autoriser les utilisateurs à ouvrir des fichiers DSL à partir de l’Explorateur Windows. Vous pouvez également associer une icône et une brève description à votre extension de nom de fichier. En outre, le MSI peut installer un XSD qui peut être utilisé pour valider des fichiers DSL. Si vous le souhaitez, vous pouvez ajouter d’autres composants à la MSI qui seront installés en même temps.

 Pour plus d’informations sur les fichiers MSI et d’autres options de déploiement, consultez [déploiement d’applications, de services et de composants](../deployment/deploying-applications-services-and-components.md).

 Pour créer un MSI, vous devez ajouter un projet d’installation à votre solution [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. La méthode la plus simple pour créer un projet d’installation consiste à utiliser le modèle CreateMsiSetupProject.tt, que vous pouvez télécharger à partir du [site VMSDK](https://go.microsoft.com/fwlink/?LinkID=186128).

#### <a name="to-deploy-a-dsl-in-an-msi"></a>Pour déployer un DSL dans un MSI

1. Définissez `InstalledByMsi` dans le manifeste de l’extension. Cela empêche l’installation et la désinstallation de la VSX, sauf par le MSI. Cela est important si vous incluez d’autres composants dans le MSI.

   1. Ouvrir DslPackage\source.extension.tt

   2. Insérez la ligne suivante avant `<SupportedProducts>`:

       ```
       <InstalledByMsi>true</InstalledByMsi>
       ```

2. Créez ou modifiez une icône qui représente votre DSL dans l’Explorateur Windows. Par exemple, modifiez **DslPackage\Resources\File.ico**

3. Assurez-vous que les attributs suivants de votre DSL sont corrects :

   - Dans l’Explorateur DSL, cliquez sur le nœud racine et, dans Fenêtre Propriétés, consultez :

       - Description

       - Version

   - Cliquez sur le nœud **éditeur** et dans le fenêtre Propriétés, cliquez sur l' **icône**. Définir la valeur pour référencer un fichier d’icône dans **DslPackage\Resources**, tel que **file. ico**

   - Dans le menu **générer** , ouvrez **Configuration Manager**, puis sélectionnez la configuration que vous souhaitez générer, par exemple **version finale** ou **débogage**.

4. Accédez à la [page d’hébergement du kit de développement logiciel de visualisation et de modélisation](https://go.microsoft.com/fwlink/?LinkID=186128), puis, sous l’onglet **téléchargements** , téléchargez **CreateMsiSetupProject.TT**.

5. Ajoutez **CreateMsiSetupProject.TT** à votre projet DSL.

    [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] créera un fichier nommé **CreateMsiSetupProject. vdproj**.

6. Dans l’Explorateur Windows, copiez DSL\\*. vdproj dans un nouveau dossier nommé Setup.

    (Si vous le souhaitez, vous pouvez maintenant exclure CreateMsiSetupProject.tt de votre projet DSL.)

7. Dans **Explorateur de solutions**, ajoutez **le programme d’installation\\\*. vdproj** en tant que projet existant.

8. Dans le menu **projet** , cliquez sur **dépendances du projet**.

    Dans la boîte de dialogue **dépendances du projet** , sélectionnez le projet d’installation.

    Activez la case à cocher en regard de **DslPackage**.

9. Régénérez la solution.

10. Dans l’Explorateur Windows, localisez le fichier MSI généré dans votre projet d’installation.

     Copiez le fichier MSI sur un ordinateur sur lequel vous souhaitez installer votre DSL. Double-cliquez sur le fichier MSI. Le programme d'installation s'exécute.

11. Sur l’ordinateur cible, créez un nouveau fichier qui a l’extension de fichier de votre DSL. Vérifiez les éléments suivants :

    - Dans le mode liste de l’Explorateur Windows, le fichier apparaît avec l’icône et la description que vous avez définies.

    - Lorsque vous double-cliquez sur le fichier, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] démarre et ouvre le fichier DSL dans votre éditeur DSL.

    Si vous préférez, vous pouvez créer le projet d’installation manuellement, au lieu d’utiliser le modèle de texte. Pour obtenir une procédure pas à pas qui comprend cette procédure, consultez le chapitre 5 du [laboratoire de visualisation et de modélisation SDK](https://go.microsoft.com/fwlink/?LinkId=208878).

#### <a name="to-uninstall-a-dsl-that-was-installed-from-an-msi"></a>Pour désinstaller un DSL qui a été installé à partir d’un MSI

1. Dans Windows, ouvrez le panneau de configuration **programmes et fonctionnalités** .

2. Désinstallez le DSL.

3. Redémarrez Visual Studio.
