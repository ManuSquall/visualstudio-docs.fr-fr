---
title: "Déploiement MSI et VSIX des DSL | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6ce16f06-1978-4e19-8cdc-441ee65a3fb2
caps.latest.revision: 2
author: alancameronwills
ms.author: awills
manager: douge
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: beb505dca6f5b52046ca87e854260f4b222079c8
ms.lasthandoff: 02/22/2017

---
# <a name="msi-and-vsix-deployment-of-a-dsl"></a>Déploiement MSI et VSIX d'un langage spécifique à un domaine
Vous pouvez installer un langage spécifique à un domaine sur votre ordinateur ou sur d’autres ordinateurs. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]doit déjà être installé sur l’ordinateur cible.  
  
##  <a name="a-namewhicha-choosing-between-vsix-and-msi-deployment"></a><a name="which"></a>Choix entre VSIX et de déploiement MSI  
 Il existe deux méthodes de déploiement d’un langage spécifique à un domaine :  
  
|Méthode|Avantages|  
|------------|--------------|  
|VSX ([!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Extension)|Très facile à déployer : copie et d’exécuter le **.vsix** fichier du projet DslPackage.<br /><br /> Pour plus d’informations, consultez [l’installation et la désinstallation d’un DSL à l’aide de la VSX](#Installing).|  
|MSI (fichier de programme d’installation)|-Permet à l’utilisateur d’ouvrir [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] en double-cliquant sur un fichier DSL.<br />-Associe une icône au type de fichier DSL dans l’ordinateur cible.<br />-Associe un XSD (schéma XML) avec le type de fichier DSL. Cela permet d’éviter les avertissements lorsque le fichier est chargé dans [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].<br /><br /> Vous devez ajouter un projet d’installation à votre solution pour créer un fichier MSI.<br /><br /> Pour plus d’informations, consultez [déploiement DSL à l’aide d’un fichier MSI](#msi).|  
  
##  <a name="a-nameinstallinga-installing-and-uninstalling-a-dsl-by-using-the-vsx"></a><a name="Installing"></a>L’installation et la désinstallation d’un DSL à l’aide de la VSX  
 Lorsque votre solution DSL est installé par cette méthode, l’utilisateur peut ouvrir un fichier DSL depuis [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], mais le fichier ne peut pas être ouvert à partir de l’Explorateur Windows.  
  
#### <a name="to-install-a-dsl-by-using-the-vsx"></a>Pour installer une solution DSL à l’aide de la VSX  
  
1.  Sur votre ordinateur, recherchez le **.vsix** fichier a été généré par votre projet de Package DSL.  
  
    1.  Dans **l’Explorateur de solutions**, avec le bouton droit le **DslPackage** de projet, puis cliquez sur **ouvrir le dossier dans l’Explorateur Windows**.  
  
    2.  Locate the file **bin\\\*\\***YourProject***. DslPackage.vsix**  
  
2.  Copie le **.vsix** fichier sur l’ordinateur cible sur lequel vous souhaitez installer la solution DSL. Il peut s’agir de votre propre ordinateur ou d’un autre.  
  
    -   L’ordinateur cible doit avoir une des éditions de [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] qui prend en charge DSL en cours d’exécution. Pour plus d’informations, consultez [prise en charge les éditions Visual Studio SDK de visualisation se modélisation](../modeling/supported-visual-studio-editions-for-visualization-amp-modeling-sdk.md).  
  
    -   L’ordinateur cible doit avoir une des éditions de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] spécifié dans **DslPackage\source.extensions.manifest**.  
  
3.  Sur l’ordinateur cible, double-cliquez sur le **.vsix** fichier.  
  
     Le**Programme d’installation des extensions Visual Studio** s’ouvre et installe l’extension.  
  
4.  Démarrez ou redémarrez [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)].  
  
5.  Pour tester la solution DSL, utilisez [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] pour créer un nouveau fichier ayant l’extension que vous avez définie pour votre DSL.  
  
#### <a name="to-uninstall-a-dsl-that-was-installed-by-using-vsx"></a>Pour désinstaller une solution DSL a été installée à l’aide de VSX  
  
1.  Sur le **outils** menu, cliquez sur **le Gestionnaire d’extensions**.  
  
2.  Développez **Extensions installées**.  
  
3.  Sélectionnez l’extension dans lequel est défini le DSL, puis cliquez sur **désinstallation**.  
  
 Exceptionnellement, une extension défaillante ne parvient pas à se charger et crée un rapport dans la fenêtre d’erreur, mais ne s’affiche pas dans le Gestionnaire d’extensions. Dans ce cas, vous pouvez supprimer l’extension en supprimant le fichier de l’emplacement suivant :  
  
 *LocalAppData* **\Microsoft\VisualStudio\10.0\Extensions**  
  
##  <a name="a-namemsia-deploying-a-dsl-in-an-msi"></a><a name="msi"></a>Déploiement d’une solution DSL dans un fichier MSI  
 Définition d’un fichier MSI (Windows Installer) pour votre DSL, vous pouvez permettre aux utilisateurs d’ouvrir des fichiers DSL à partir de l’Explorateur Windows. Vous pouvez également associer une icône et une brève description votre extension de nom de fichier. En outre, le fichier MSI peut installer un XSD qui peut être utilisé pour valider des fichiers DSL. Si vous le souhaitez, vous pouvez ajouter d’autres composants dans le fichier MSI qui sera installé en même temps.  
  
 Pour plus d’informations sur les fichiers MSI et d’autres options de déploiement, consultez la page [déploiement d’Applications, Services et composants](../deployment/deploying-applications-services-and-components.md).  
  
 Pour générer un fichier MSI, vous ajoutez un projet d’installation pour votre [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] solution. La méthode la plus simple de créer un projet d’installation consiste à utiliser le modèle CreateMsiSetupProject.tt, que vous pouvez télécharger à partir de la [site VMSDK](http://go.microsoft.com/fwlink/?LinkID=186128).  
  
#### <a name="to-deploy-a-dsl-in-an-msi"></a>Pour déployer une solution DSL dans un fichier MSI  
  
1.  Définissez `InstalledByMsi` dans le manifeste de l’extension. Cela empêche le VSX installé et désinstallé, sauf par le fichier MSI. Ceci est important si vous incluez les autres composants dans le fichier MSI.  
  
    1.  Ouvrez DslPackage\source.extension.tt  
  
    2.  Insérez la ligne suivante avant de `<SupportedProducts>`:  
  
        ```  
        <InstalledByMsi>true</InstalledByMsi>  
        ```  
  
2.  Créer ou modifier une icône qui représente votre DSL dans l’Explorateur Windows. Par exemple, modifier **DslPackage\Resources\File.ico**  
  
3.  Assurez-vous que les attributs suivants de votre DSL sont corrects :  
  
    -   Cliquez sur le nœud racine dans l’Explorateur DSL et dans la fenêtre Propriétés, consultez :  
  
        -   Description  
  
        -   Version  
  
    -   Cliquez sur le **éditeur** nœud dans la fenêtre Propriétés, cliquez sur **icône**. Définissez la valeur pour référencer un fichier d’icône **DslPackage\Resources**, tel que **File.ico**  
  
    -   Sur le **Build** menu, ouvrez **Configuration Manager**et sélectionnez la configuration que vous souhaitez générer, tel que **version** ou **Debug**.  
  
4.  Accédez à [page d’accueil Visualization and Modeling SDK](http://go.microsoft.com/fwlink/?LinkID=186128)et à partir de la **télécharge** onglet, téléchargez **CreateMsiSetupProject.tt**.  
  
5.  Ajouter **CreateMsiSetupProject.tt** à votre projet Dsl.  
  
     [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]Crée un fichier nommé **CreateMsiSetupProject.vdproj**.  
  
6.  Dans l’Explorateur Windows, copiez Dsl\\*.vdproj vers un nouveau dossier nommé le programme d’installation.  
  
     (Si vous le souhaitez, vous pouvez désormais exclure CreateMsiSetupProject.tt à partir de votre projet Dsl.)  
  
7.  Dans **l’Explorateur de solutions**, ajoutez **le programme d’installation\\\*.vdproj** qu’un projet existant.  
  
8.  Sur le **projet** menu, cliquez sur **dépendances du projet**.  
  
     Dans le **dépendances du projet** boîte de dialogue, sélectionnez le projet d’installation.  
  
     Activez la case à côté **DslPackage**.  
  
9. Régénérez la solution.  
  
10. Dans l’Explorateur Windows, recherchez le fichier MSI généré dans votre projet d’installation.  
  
     Copiez le fichier MSI sur un ordinateur sur lequel vous voulez installer votre DSL. Double-cliquez sur le fichier MSI. Le programme d’installation s’exécute.  
  
11. Sur l’ordinateur cible, créez un fichier qui porte l’extension de votre DSL. Vérifiez que :  
  
    -   Dans la vue liste de l’Explorateur Windows, le fichier s’affiche avec l’icône et la description que vous avez définie.  
  
    -   Lorsque vous double-cliquez sur le fichier, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] démarre et ouvre le fichier DSL dans l’éditeur de votre DSL.  
  
 Si vous préférez, vous pouvez créer le projet d’installation manuellement, au lieu d’utiliser le modèle de texte. Pour une procédure pas à pas qui inclut cette procédure, reportez-vous au chapitre 5 de la [de visualisation et de modélisation de laboratoire de SDK](http://go.microsoft.com/fwlink/?LinkId=208878).  
  
#### <a name="to-uninstall-a-dsl-that-was-installed-from-an-msi"></a>Pour désinstaller une solution DSL a été installée à partir d’un fichier MSI  
  
1.  Dans Windows, ouvrez le **programmes et fonctionnalités** le panneau de configuration.  
  
2.  Désinstaller la solution DSL.  
  
3.  Redémarrez Visual Studio.
