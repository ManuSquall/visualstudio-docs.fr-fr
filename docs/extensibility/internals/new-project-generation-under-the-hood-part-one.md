---
title: "Nouvelle génération de projet : Dans les coulisses, première partie | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- projects [Visual Studio], new project dialog
- projects [Visual Studio], new project generation
ms.assetid: 66778698-0258-467d-8b8b-c351744510eb
caps.latest.revision: "29"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: efe08d9e23f1a77fd68df2bdba4389e7b7955b11
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="new-project-generation-under-the-hood-part-one"></a>Nouvelle génération de projet : Dans les coulisses, première partie
Jamais vu comment créer votre propre type de projet ? Demandez que se passe-t-il réellement lorsque vous créez un nouveau projet ? Nous allons jeter un coup sous le capot et voir ce qui se passe vraiment.  
  
 Il existe plusieurs tâches que les coordonnées de Visual Studio pour vous :  
  
-   Il affiche une arborescence de tous les types de projet disponibles.  
  
-   Il affiche la liste des modèles d’application pour chaque type de projet et vous permet de choisir un.  
  
-   Il collecte des informations de projet pour l’application, telles que le nom du projet et le chemin d’accès.  
  
-   Il transmet ces informations à la fabrique de projets.  
  
-   Il génère des éléments de projet et des dossiers dans la solution actuelle.  
  
## <a name="the-new-project-dialog-box"></a>La boîte de dialogue Nouveau projet  
 Tout commence lorsque vous sélectionnez un type de projet pour un nouveau projet. Nous allons commencer en cliquant sur **nouveau projet** sur la **fichier** menu. Le **nouveau projet** boîte de dialogue s’affiche, recherche quelque chose comme ceci :  
  
 ![Boîte de dialogue Nouveau projet](../../extensibility/internals/media/newproject.gif "NewProject")  
  
 Jetons un œil plus proche. Le **types de projet** les différents types de projet, vous pouvez créer des listes d’arborescence. Lorsque vous sélectionnez un type de projet comme **Windows Visual c#**, vous voyez une liste des modèles d’application pour vous aider à démarrer. **Modèles Visual Studio installés** sont installés par Visual Studio et sont disponibles pour tout utilisateur de votre ordinateur. Nouveaux modèles que vous créez ou collectez peuvent être ajoutés à **Mes modèles** et sont disponibles uniquement pour vous.  
  
 Lorsque vous sélectionnez un modèle comme **Application Windows**, une description du type d’application s’affiche dans la boîte de dialogue, dans ce cas, **un projet de création d’une application avec une interface utilisateur Windows**.  
  
 Au bas de la **nouveau projet** boîte de dialogue, vous verrez plusieurs contrôles qui collecter plus d’informations. Les contrôles que vous voyez varient selon le type de projet, mais elles comprennent en général d’un projet **nom** zone de texte, un **emplacement** zone de texte et connexes **Parcourir** bouton et un **Nom de la solution** zone de texte et connexes **créer le répertoire pour la solution** case à cocher.  
  
## <a name="populating-the-new-project-dialog-box"></a>Remplissage de la boîte de dialogue Nouveau projet  
 Où est le **nouveau projet** boîte de dialogue obtenir ses informations à partir de ? Il existe deux mécanismes dans ce cas précis, un d’eux déconseillée. Le **nouveau projet** combine de boîte de dialogue et affiche les informations obtenues à partir de ces deux mécanismes.  
  
 L’ancienne méthode (déconseillée) utilise les entrées du Registre système et les fichiers .vsdir. Ce mécanisme s’exécute à l’ouverture de Visual Studio. La méthode la plus récente utilise des fichiers .vstemplate. Ce mécanisme s’exécute lors de l’initialisation de Visual Studio, par exemple, en exécutant  
  
```  
devenv /setup  
```  
  
 ou  
  
```  
devenv /installvstemplates  
```  
  
### <a name="project-types"></a>Types de projet  
 La position et les noms de la **types de projet** racine des nœuds, tels que **Visual C#** et **autres langages**, est déterminée par les entrées du Registre système. L’organisation des nœuds enfants, tels que **base de données** et **Smart Device**, reflète la hiérarchie des dossiers qui contiennent les fichiers .vstemplate correspondant. Examinons les nœuds racines tout d’abord.  
  
#### <a name="project-type-root-nodes"></a>Nœuds de racines de Type de projet  
 Lorsque [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] est initialisé, il parcourt les sous-clés de la clé de Registre système HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\14.0\NewProjectTemplates\TemplateDirs pour créer et nommer les nœuds racines de la **detypesdeprojets** arborescence. Cette information est mis en cache pour une utilisation ultérieure. Examinez le TemplateDirs\\{FAE04EC1-301F-11D3-BF4B-00C04F79EFBC} \\ /1 clé. Chaque entrée est un GUID VSPackage. Le nom de la sous-clé (/ 1) est ignoré, mais sa présence indique qu’il s’agit d’un **types de projet** nœud racine. Un nœud racine peut avoir à son tour plusieurs sous-clés qui contrôlent son apparence dans le **types de projet** arborescence. Examinons certains d'entre eux.  
  
##### <a name="default"></a>(Default)  
 Il s’agit de l’ID de ressource de la chaîne localisée que les noms du nœud racine. La ressource de chaîne se trouve dans la DLL sélectionné par le GUID VSPackage satellite.  
  
 Dans l’exemple, le GUID de VSPackage est  
  
 {FAE04EC1-301F-11D3-BF4B-00C04F79EFBC}  
  
 et l’ID de ressource (valeur par défaut) du nœud racine (/ 1) est #2345  
  
 Si vous recherchez le GUID dans la clé de Packages à proximité et examinez la sous-clé SatelliteDll, vous trouverez le chemin d’accès de l’assembly qui contient la ressource de chaîne :  
  
 \<Le chemin d’accès de Visual Studio installation > \VC#\VCSPackages\1033\csprojui.dll  
  
 Pour vérifier cela, ouvrez l’Explorateur de fichiers et faites glisser csprojui.dll dans le répertoire Visual Studio... La table de chaînes montre que la ressource #2345 a la légende **Visual C#**.  
  
##### <a name="sortpriority"></a>SortPriority  
 Ce paramètre détermine la position du nœud racine dans le **types de projet** arborescence.  
  
 SortPriority REG_DWORD 0x00000014 (20)  
  
 Plus le nombre de priorité, plus la position dans l’arborescence.  
  
##### <a name="developeractivity"></a>DeveloperActivity  
 Si cette sous-clé est présente, la position du nœud racine est contrôlée par la boîte de dialogue Paramètres de développeur. Par exemple :  
  
 DeveloperActivity REG_SZ VC #  
  
 Indique que Visual c# est un nœud racine si Visual Studio est définie pour [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] développement. Dans le cas contraire, il sera un nœud enfant de **autres langages**.  
  
##### <a name="folder"></a>Dossier  
 Si cette sous-clé est présente, le nœud racine devienne un nœud enfant du dossier spécifié. Une liste de dossiers possibles s’affiche sous la clé  
  
 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\11.0\NewProjectTemplates\PseudoFolders  
  
 Par exemple, l’entrée de projets de base de données a une clé de dossier qui correspond à l’entrée d’autres Types de projets dans PseudoFolders. Ainsi, dans le **types de projet** arborescence, **des projets de base de données** sera un nœud enfant de **autres Types de projets**.  
  
#### <a name="project-type-child-nodes-and-vstdir-files"></a>Type des nœuds enfants et les fichiers .vstdir de projet  
 La position des nœuds enfants dans le **types de projet** arborescence suit la hiérarchie des dossiers dans les dossiers ProjectTemplates. Pour les modèles d’ordinateur (**modèles Visual Studio installés**), l’emplacement par défaut est \Program Files\Microsoft Visual Studio 14.0\Common7\IDE\ProjectTemplates\ et pour les modèles de l’utilisateur (**Mes modèles**), l’emplacement par défaut est documents\Visual Studio 14.0\Templates\ProjectTemplates\\. Les hiérarchies de dossier à partir de ces deux emplacements sont fusionnés pour créer le **types de projet** arborescence.  
  
 Pour Visual Studio c# Paramètres du développeur, la **types de projet** arborescence ressemble à ceci :  
  
 ![Types de projets](../../extensibility/internals/media/projecttypes.png "ProjectTypes")  
  
 Le dossier ProjectTemplates correspondant ressemble à ceci :  
  
 ![Modèles de projet](../../extensibility/internals/media/projecttemplates.png "ProjectTemplates")  
  
 Lorsque le **nouveau projet** boîte de dialogue s’ouvre, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] traverse le dossier ProjectTemplates et recrée la structure dans le **types de projet** arborescence avec des modifications :  
  
-   Le nœud racine de la **types de projet** arborescence est déterminée par le modèle d’application.  
  
-   Le nom du nœud peut être localisé et peut contenir des caractères spéciaux.  
  
-   L’ordre de tri peut être modifié.  
  
##### <a name="finding-the-root-node-for-a-project-type"></a>Recherche le nœud racine pour un Type de projet  
 Quand Visual Studio traverse les dossiers ProjectTemplates, il ouvre tous les fichiers .zip et extrait les fichiers .vstemplate. Un fichier .vstemplate utilise XML pour décrire un modèle d’application. Pour plus d’informations, consultez [nouvelle génération de projet : sous le capot, partie deux](../../extensibility/internals/new-project-generation-under-the-hood-part-two.md).  
  
 Le \<ProjectType > balise détermine le type de projet pour l’application. Par exemple, le fichier \CSharp\SmartDevice\WindowsCE\1033\WindowsCE-EmptyProject.zip contient un fichier de EmptyProject.vstemplate ayant cette balise :  
  
```  
<ProjectType>CSharp</ProjectType>  
```  
  
 Le \<ProjectType > balise et pas le sous-dossier dans le dossier ProjectTemplates, détermine le nœud racine de l’application dans le **types de projet** arborescence. Dans l’exemple, les applications Windows CE apparaîtraient sous la **Visual C#** nœud racine, et même si vous deviez déplacer le dossier WindowsCE dans le dossier Visual Basic, les applications Windows CE seraient apparaissent toujours sous la  **Visual C#** nœud racine.  
  
##### <a name="localizing-the-node-name"></a>Localisation du nom de nœud  
 Quand Visual Studio traverse les dossiers ProjectTemplates, il examine tous les fichiers .vstdir qu’il trouve. Un fichier .vstdir est un fichier XML qui contrôle l’apparence du type de projet dans le **nouveau projet** boîte de dialogue. Dans le fichier .vstdir, utilisez le \<LocalizedName > balise au nom de la **types de projet** nœud.  
  
 Par exemple, le fichier \CSharp\Database\TemplateIndex.vstdir contient cette balise :  
  
```  
<LocalizedName Package="{462b036f-7349-4835-9e21-bec60e989b9c}" ID="4598"/>  
```  
  
 Ce paramètre détermine l’ID de ressources et les DLL satellite de la chaîne localisée qui dans ce cas, le nœud racine, les noms **base de données**. Le nom localisé peut contenir des caractères spéciaux qui ne sont pas disponibles pour les noms de dossier, tel que **.NET**.  
  
 Si aucun \<LocalizedName > balise est présent, le type de projet est nommé par le dossier lui-même, **SmartPhone2003**.  
  
##### <a name="finding-the-sort-order-for-a-project-type"></a>Recherche de l’ordre de tri pour un Type de projet  
 Pour déterminer l’ordre de tri du type de projet, utilisent les fichiers .vstdir le \<SortOrder > balise.  
  
 Par exemple, le fichier \CSharp\Windows\Windows.vstdir contient cette balise :  
  
```  
<SortOrder>5</SortOrder>  
```  
  
 Le fichier \CSharp\Database\TemplateIndex.vstdir a une balise avec une valeur supérieure :  
  
```  
<SortOrder>5000</SortOrder>  
```  
  
 Plus le nombre dans le \<SortOrder > balise, plus la position dans l’arborescence, afin que la **Windows** nœud apparaît supérieure à la **base de données** nœud dans le **types de projets**  arborescence.  
  
 Si aucun \<SortOrder > balise est spécifiée pour un type de projet, il apparaît dans l’ordre alphabétique en suivant les types de projets qui contiennent des \<SortOrder > spécifications.  
  
 Notez qu’il n’y a aucun fichier .vstdir dans Mes Documents (**Mes modèles**) dossiers. Les noms de type de projet application utilisateur ne sont pas localisés et s’affichent dans l’ordre alphabétique.  
  
#### <a name="a-quick-review"></a>Une révision rapide  
 Nous allons modifier le **nouveau projet** boîte de dialogue zone et créer un modèle de projet utilisateur.  
  
1.  Ajouter un sous-dossier MyProjectNode vers le dossier \Program Files\Microsoft Visual Studio 14.0\Common7\IDE\ProjectTemplates\CSharp.  
  
2.  Créer un fichier MyProject.vstdir dans le dossier MyProjectNode à l’aide de n’importe quel éditeur de texte.  
  
3.  Ajoutez ces lignes au fichier .vstdir :  
  
    ```  
    <TemplateDir Version="1.0.0">  
        <SortOrder>6</SortOrder>  
    </TemplateDir>  
    ```  
  
4.  Enregistrez et fermez le fichier .vstdir.  
  
5.  Créer un fichier MyProject.vstemplate dans le dossier MyProjectNode à l’aide de n’importe quel éditeur de texte.  
  
6.  Ajoutez ces lignes au fichier .vstemplate :  
  
    ```  
    <VSTemplate Version="2.0.0" Type="Project" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
        <TemplateData>  
            <ProjectType>CSharp</ProjectType>  
        </TemplateData>  
    </VSTemplate>  
    ```  
  
7.  Enregistrez le fichier de the.vstemplate et fermez l’éditeur.  
  
8.  Envoyer le fichier .vstemplate dans un nouveau dossier MyProjectNode\MyProject.zip compressé.  
  
9. À partir de la fenêtre de commande Visual Studio, tapez :  
  
    ```  
    devenv /installvstemplates  
    ```  
  
 Ouvrez Visual Studio.  
  
1.  Ouvrez le **nouveau projet** boîte de dialogue zone, puis développez le **Visual C#** le nœud de projet.  
  
 ![MyProjectNode](../../extensibility/internals/media/myprojectnode.png "MyProjectNode")  
  
 **MyProjectNode** apparaît sous la forme d’un nœud enfant de Visual C# juste sous le nœud de Windows.  
  
## <a name="see-also"></a>Voir aussi  
 [Génération de nouveau projet : les rouages du système, partie 2](../../extensibility/internals/new-project-generation-under-the-hood-part-two.md)