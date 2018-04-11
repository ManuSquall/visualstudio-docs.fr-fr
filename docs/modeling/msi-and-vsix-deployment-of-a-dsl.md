---
title: MSI et le déploiement VSIX de DSL | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.topic: article
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: de6b219610908503f37658ff977f042363fb8663
ms.sourcegitcommit: 3b692c9bf332b7b9150901e16daf99a64b599fee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/10/2018
---
# <a name="msi-and-vsix-deployment-of-a-dsl"></a>Déploiement MSI et VSIX d'un langage spécifique à un domaine
Vous pouvez installer un langage spécifique à un domaine sur votre ordinateur ou sur d’autres ordinateurs. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] doit déjà être installé sur l’ordinateur cible.  
  
##  <a name="which"></a> Choix entre VSIX et de déploiement MSI  
 Il existe deux méthodes de déploiement d’un langage spécifique à un domaine :  
  
|Méthode|Avantages|  
|------------|--------------|  
|VSX ([!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Extension)|Très facile à déployer : copie et d’exécuter le **.vsix** fichier à partir du projet DslPackage.<br /><br /> Pour plus d’informations, consultez [installation et désinstallation d’une DSL à l’aide de la VSX](#Installing).|  
|MSI (fichier de programme d’installation)|: Permet d’ouvrir [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] en double-cliquant sur un fichier DSL.<br />-Associe une icône avec le type de fichier DSL sur l’ordinateur cible.<br />-Associe un schéma XSD (schéma XML) avec le type de fichier DSL. Cela évite des avertissements lorsque le fichier est chargé dans [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].<br /><br /> Vous devez ajouter un projet d’installation à votre solution pour créer un fichier MSI.<br /><br /> Pour plus d’informations, consultez [déploiement DSL à l’aide d’un fichier MSI](#msi).|  
  
##  <a name="Installing"></a> Installation et désinstallation d’une DSL à l’aide de la VSX  
 Lorsque votre DSL est installé par cette méthode, l’utilisateur peut ouvrir un fichier DSL depuis [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], mais le fichier ne peut pas être ouverte à partir de l’Explorateur Windows.  
  
#### <a name="to-install-a-dsl-by-using-the-vsx"></a>Pour installer une DSL à l’aide de la VSX  
  
1.  Sur votre ordinateur, recherchez le **.vsix** fichier qui a été généré par votre projet de Package de DSL.  
  
    1.  Dans **l’Explorateur de solutions**, cliquez sur le **DslPackage** de projet, puis cliquez sur **ouvrir le dossier dans l’Explorateur Windows**.  
  
    2.  Recherchez le fichier **bin\\\*\\***VotreProjet***. DslPackage.vsix**  
  
2.  Copie le **.vsix** fichier à l’ordinateur cible sur lequel vous souhaitez installer le DSL. Il peut s’agir de votre propre ordinateur ou d’un autre.  
  
    -   L’ordinateur cible doit avoir l’une des éditions de [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] qui prend en charge DSL en cours d’exécution. Pour plus d’informations, consultez [pris en charge les éditions Visual Studio pour la visualisation et modélisation de kit de développement logiciel](../modeling/supported-visual-studio-editions-for-visualization-amp-modeling-sdk.md).  
  
    -   L’ordinateur cible doit avoir l’une des éditions de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] spécifié dans **DslPackage\source.extensions.manifest**.  
  
3.  Sur l’ordinateur cible, double-cliquez sur le **.vsix** fichier.  
  
     Le**Programme d’installation des extensions Visual Studio** s’ouvre et installe l’extension.  
  
4.  Démarrez ou redémarrez [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)].  
  
5.  Pour tester la DSL, utilisez [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] pour créer un nouveau fichier ayant l’extension que vous avez définie pour votre DSL.  
  
#### <a name="to-uninstall-a-dsl-that-was-installed-by-using-vsx"></a>Pour désinstaller une DSL a été installée à l’aide de VSX  
  
1.  Sur le **outils** menu, cliquez sur **Gestionnaire d’extensions**.  
  
2.  Développez **Extensions installées**.  
  
3.  Sélectionnez l’extension dans laquelle la DSL est définie, puis cliquez sur **désinstallation**.  
  
 Exceptionnellement, une extension défaillante ne parvient pas à se charger et crée un rapport dans la fenêtre d’erreur, mais ne s’affiche pas dans le Gestionnaire d’extensions. Dans ce cas, vous pouvez supprimer l’extension en supprimant le fichier de l’emplacement suivant :  
  
 *LocalAppData* **\Microsoft\VisualStudio\10.0\Extensions**  
  
##  <a name="msi"></a> Déploiement DSL dans un fichier MSI  
 En définissant un fichier MSI (Windows Installer) de votre DSL, vous pouvez autoriser les utilisateurs à ouvrir des fichiers DSL à partir de l’Explorateur Windows. Vous pouvez également associer une icône et une brève description votre extension de nom de fichier. En outre, le fichier MSI peut installer un schéma XSD qui peut être utilisé pour valider les fichiers DSL. Si vous le souhaitez, vous pouvez ajouter d’autres composants dans le fichier MSI qui vont être installé en même temps.  
  
 Pour plus d’informations sur les fichiers MSI et d’autres options de déploiement, consultez [déploiement d’Applications, Services et composants](../deployment/deploying-applications-services-and-components.md).  
  
 Pour générer un fichier MSI, vous ajoutez un projet d’installation pour votre [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] solution. La méthode de création d’un projet d’installation la plus simple est d’utiliser le modèle CreateMsiSetupProject.tt, que vous pouvez télécharger à partir de la [site VMSDK](http://go.microsoft.com/fwlink/?LinkID=186128).  
  
#### <a name="to-deploy-a-dsl-in-an-msi"></a>Pour déployer une DSL dans un fichier MSI  
  
1.  Définissez `InstalledByMsi` dans le manifeste d’extension. Cela empêche le VSX installé et désinstallé à l’exception par le fichier MSI. Ceci est important si vous inclurez les autres composants dans le fichier MSI.  
  
    1.  Ouvrez DslPackage\source.extension.tt  
  
    2.  Insérez la ligne suivante avant de `<SupportedProducts>`:  
  
        ```  
        <InstalledByMsi>true</InstalledByMsi>  
        ```  
  
2.  Créez ou modifiez une icône qui représente votre DSL dans l’Explorateur Windows. Par exemple, modifiez **DslPackage\Resources\File.ico**  
  
3.  Assurez-vous que les attributs suivants de votre DSL sont corrects :  
  
    -   Cliquez sur le nœud racine dans l’Explorateur DSL et dans la fenêtre Propriétés, consultez :  
  
        -   Description  
  
        -   Version  
  
    -   Cliquez sur le **éditeur** nœud dans la fenêtre Propriétés, cliquez sur **icône**. Définir la valeur pour faire référence à un fichier d’icône **DslPackage\Resources**, tel que **File.ico**  
  
    -   Sur le **générer** menu, ouvrir **Configuration Manager**, puis sélectionnez la configuration que vous souhaitez générer, tel que **version** ou **déboguer** .  
  
4.  Accédez à [page d’accueil Visualization and Modeling SDK](http://go.microsoft.com/fwlink/?LinkID=186128)et à partir de la **télécharge** onglet, téléchargez **CreateMsiSetupProject.tt**.  
  
5.  Ajouter **CreateMsiSetupProject.tt** à votre projet Dsl.  
  
     [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Crée un fichier nommé **CreateMsiSetupProject.vdproj**.  
  
6.  Dans l’Explorateur Windows, copiez Dsl\\*.vdproj vers un nouveau dossier nommé le programme d’installation.  
  
     (Si vous le souhaitez, vous pouvez désormais exclure CreateMsiSetupProject.tt à partir de votre projet Dsl.)  
  
7.  Dans **l’Explorateur de solutions**, ajoutez **le programme d’installation\\\*.vdproj** qu’un projet existant.  
  
8.  Sur le **projet** menu, cliquez sur **dépendances du projet**.  
  
     Dans le **dépendances du projet** boîte de dialogue, sélectionnez le projet d’installation.  
  
     Activez la case à côté **DslPackage**.  
  
9. Régénérez la solution.  
  
10. Dans l’Explorateur Windows, recherchez le fichier MSI généré dans votre projet d’installation.  
  
     Copiez le fichier MSI sur un ordinateur sur lequel vous voulez installer votre DSL. Double-cliquez sur le fichier MSI. Le programme d’installation s’exécute.  
  
11. Dans l’ordinateur cible, créez un nouveau fichier qui porte l’extension de fichier de votre DSL. Vérifiez que :  
  
    -   Dans la vue liste de l’Explorateur Windows, le fichier s’affiche avec l’icône et la description que vous avez définie.  
  
    -   Lorsque vous double-cliquez sur le fichier, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] démarre et ouvre le fichier DSL dans l’éditeur de votre DSL.  
  
 Si vous préférez, vous pouvez créer le projet d’installation manuellement, au lieu d’utiliser le modèle de texte. Pour une procédure pas à pas qui inclut cette procédure, consultez le chapitre 5 du [de visualisation et de modélisation de laboratoire de kit de développement logiciel](http://go.microsoft.com/fwlink/?LinkId=208878).  
  
#### <a name="to-uninstall-a-dsl-that-was-installed-from-an-msi"></a>Pour désinstaller une DSL a été installée à partir d’un fichier MSI  
  
1.  Dans Windows, ouvrez le **programmes et fonctionnalités** le panneau de configuration.  
  
2.  Désinstallez la DSL.  
  
3.  Redémarrez Visual Studio.