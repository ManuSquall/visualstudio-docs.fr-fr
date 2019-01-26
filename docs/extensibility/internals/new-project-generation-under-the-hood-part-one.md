---
title: 'Nouvelle génération de projet : Sous le capot, première partie | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio], new project dialog
- projects [Visual Studio], new project generation
ms.assetid: 66778698-0258-467d-8b8b-c351744510eb
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dd41bb8fd0e35ee13815b11941950d9031f824a0
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "55041787"
---
# <a name="new-project-generation-under-the-hood-part-one"></a>Nouvelle génération de projet : Sous le capot, première partie
Jamais pensé que sur la façon de créer votre propre type de projet ? Vous vous demandez ce qui se passe réellement lorsque vous créez un nouveau projet ? Prenons un œil en coulisses et voyons ce qui se passe vraiment.  
  
 Il existe plusieurs tâches qui coordonne les Visual Studio pour vous :  
  
-   Il affiche une arborescence de tous les types de projet disponibles.  
  
-   Il affiche la liste des modèles d’application pour chaque type de projet et vous permet de choisir un.  
  
-   Il collecte des informations de projet pour l’application, telles que le nom du projet et le chemin d’accès.  
  
-   Il transmet ces informations à la fabrique de projets.  
  
-   Il génère des éléments de projet et des dossiers dans la solution actuelle.  
  
## <a name="the-new-project-dialog-box"></a>La boîte de dialogue Nouveau projet  
 Tout commence lorsque vous sélectionnez un type de projet pour un nouveau projet. Nous allons commencer en cliquant sur **nouveau projet** sur le **fichier** menu. Le **nouveau projet** boîte de dialogue s’affiche, qui recherchent quelque chose comme suit :  
  
 ![Boîte de dialogue Nouveau projet](../../extensibility/internals/media/newproject.gif "NewProject")  
  
 Examinons plus en détail. Le **types de projets** arborescence répertorie les différents types de projet, vous pouvez créer. Lorsque vous sélectionnez un type de projet comme **Visual C# Windows**, vous verrez une liste des modèles d’application pour vous aider à démarrer. **Modèles Visual Studio installés** sont installés par Visual Studio et sont disponibles pour tout utilisateur de votre ordinateur. Nouveaux modèles que vous créez ou collectez peuvent être ajoutés aux **Mes modèles** et sont disponibles uniquement pour vous.  
  
 Lorsque vous sélectionnez un modèle comme **Windows Application**, une description du type d’application s’affiche dans la boîte de dialogue, dans ce cas, **un projet de création d’une application avec une interface utilisateur de Windows**.  
  
 En bas de la **nouveau projet** boîte de dialogue, vous verrez plusieurs contrôles qui collecter plus d’informations. Les contrôles que vous voyez varient selon le type de projet, mais en règle générale, ils incluent un projet **nom** zone de texte, un **emplacement** zone de texte et connexes **Parcourir** bouton et un **Nom de la solution** zone de texte et connexes **créer le répertoire pour la solution** case à cocher.  
  
## <a name="populating-the-new-project-dialog-box"></a>Remplissage de la boîte de dialogue Nouveau projet  
 Où est le **nouveau projet** boîte de dialogue obtenir ses informations à partir de ? Il existe deux mécanismes au travail ici, un d’eux déconseillé. Le **nouveau projet** boîte de dialogue combine et affiche les informations obtenues à partir de ces deux mécanismes.  
  
 L’ancienne méthode (obsolète) utilise les entrées du Registre système et les fichiers .vsdir. Ce mécanisme s’exécute à l’ouverture de Visual Studio. La méthode la plus récente utilise des fichiers .vstemplate. Ce mécanisme s’exécute lors de l’initialisation de Visual Studio, par exemple, en exécutant  
  
```  
devenv /setup  
```  
  
 ou  
  
```  
devenv /installvstemplates  
```  
  
### <a name="project-types"></a>Types de projet  
 La position et les noms de la **types de projets** racine des nœuds, tels que **Visual C#** et **autres langages**, est déterminée par les entrées du Registre système. L’organisation des nœuds enfants, tels que **base de données** et **Smart Device**, reflète la hiérarchie des dossiers qui contiennent les fichiers .vstemplate correspondante. Examinons tout d’abord sur les nœuds racine.  
  
#### <a name="project-type-root-nodes"></a>Nœuds de racines de Type de projet  
 Lorsque [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] est initialisé, il parcourt les sous-clés de la clé de Registre système HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\14.0\NewProjectTemplates\TemplateDirs pour créer et nommer les nœuds racine de la **detypesdeprojets** arborescence. Ces informations sont mis en cache pour une utilisation ultérieure. Examinez le TemplateDirs\\{FAE04EC1-301F-11D3-BF4B-00C04F79EFBC} \\ /1 clé. Chaque entrée est un GUID de VSPackage. Le nom de la sous-clé (/ 1) est ignoré, mais sa présence indique qu’il s’agit d’un **types de projets** nœud racine. Un nœud racine peut avoir à son tour plusieurs sous-clés qui contrôlent son apparence dans le **types de projets** arborescence. Examinons certaines d'entre elles.  
  
##### <a name="default"></a>(Default)  
 Il s’agit de l’ID de ressource de la chaîne localisée qui nomme le nœud racine. La ressource de chaîne se trouve dans la DLL sélectionné par le GUID du VSPackage satellite.  
  
 Dans l’exemple, le GUID de VSPackage est  
  
 {FAE04EC1-301F-11D3-BF4B-00C04F79EFBC}  
  
 et l’ID de ressource (valeur par défaut) du nœud racine (/ 1) est #2345  
  
 Si vous recherchez le GUID dans la clé de Packages à proximité et examinez la sous-clé SatelliteDll, vous trouverez le chemin d’accès de l’assembly qui contient la ressource de chaîne :  
  
 \<Le chemin d’accès de Visual Studio installation > \VC#\VCSPackages\1033\csprojui.dll  
  
 Pour vérifier cela, ouvrez l’Explorateur de fichiers et faites glisser csprojui.dll dans le répertoire Visual Studio... La table de chaînes montre que les ressources #2345 porte la légende **Visual C#**.  
  
##### <a name="sortpriority"></a>SortPriority  
 Ce paramètre détermine la position du nœud racine dans le **types de projets** arborescence.  
  
 REG_DWORD SortPriority 0x00000014 (20)  
  
 Plus le nombre de priorité, plus la position dans l’arborescence.  
  
##### <a name="developeractivity"></a>DeveloperActivity  
 Si cette sous-clé est présente, la position du nœud racine est contrôlée par la boîte de dialogue Paramètres du développeur. Par exemple :  
  
 DeveloperActivity REG_SZ VC #  
  
 Indique que Visual c# est un nœud racine si Visual Studio est configuré pour [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] développement. Sinon, il sera un nœud enfant du **autres langages**.  
  
##### <a name="folder"></a>Dossier  
 Si cette sous-clé est présente, le nœud racine devienne un nœud enfant du dossier spécifié. Une liste de dossiers possibles s’affiche sous la clé  
  
 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\11.0\NewProjectTemplates\PseudoFolders  
  
 Par exemple, l’entrée de projets de base de données a une clé de dossier qui correspond à l’entrée d’autres Types de projets dans PseudoFolders. Ainsi, dans le **types de projets** arborescence, **des projets de base de données** sera un nœud enfant du **autres Types de projets**.  
  
#### <a name="project-type-child-nodes-and-vstdir-files"></a>Nœuds enfants de Type projet et les fichiers .vstdir  
 La position des nœuds enfants dans le **types de projets** arborescence suit la hiérarchie des dossiers dans les dossiers ProjectTemplates. Pour les modèles d’ordinateur (**modèles Visual Studio installés**), l’emplacement par défaut est \Program Files\Microsoft Visual Studio 14.0\Common7\IDE\ProjectTemplates\ et des modèles utilisateur (**Mes modèles**), l’emplacement par défaut est documents\Visual Studio 14.0\Templates\ProjectTemplates\\. Les hiérarchies de dossiers à partir de ces deux emplacements sont fusionnés pour créer le **types de projets** arborescence.  
  
 Pour Visual Studio avec des paramètres de développeur c#, le **types de projets** arborescence ressemble à ceci :  
  
 ![Types de projets](../../extensibility/internals/media/projecttypes.png "ProjectTypes")  
  
 Le dossier ProjectTemplates correspondant ressemble à ceci :  
  
 ![Modèles de projet](../../extensibility/internals/media/projecttemplates.png "ProjectTemplates")  
  
 Lorsque le **nouveau projet** boîte de dialogue s’ouvre, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] traverse le dossier ProjectTemplates et recrée sa structure dans le **types de projets** arborescence avec des modifications :  
  
-   Le nœud racine dans le **types de projets** arborescence est déterminée par le modèle d’application.  
  
-   Le nom du nœud peut être localisé et peut contenir des caractères spéciaux.  
  
-   L’ordre de tri peut être modifié.  
  
##### <a name="finding-the-root-node-for-a-project-type"></a>Recherche le nœud racine pour un Type de projet  
 Lorsque Visual Studio parcourt les dossiers ProjectTemplates, il ouvre tous les fichiers .zip et extrait tous les fichiers .vstemplate. Un fichier .vstemplate utilise XML pour décrire un modèle d’application. Pour plus d’informations, consultez [nouvelle génération de projet : Sous le capot, deuxième partie](../../extensibility/internals/new-project-generation-under-the-hood-part-two.md).  
  
 Le \<ProjectType > balise détermine le type de projet pour l’application. Par exemple, le fichier \CSharp\SmartDevice\WindowsCE\1033\WindowsCE-EmptyProject.zip contient un fichier EmptyProject.vstemplate qui a cette balise :  
  
```  
<ProjectType>CSharp</ProjectType>  
```  
  
 Le \<ProjectType > balise et pas le sous-dossier dans le dossier ProjectTemplates, détermine le nœud racine de l’application dans le **types de projets** arborescence. Dans l’exemple, les applications Windows CE apparaîtraient sous la **Visual C#** nœud racine, et même si vous deviez déplacer le dossier WindowsCE vers le dossier de Visual Basic, les applications Windows CE seraient apparaissent toujours sous le  **Visual C#** nœud racine.  
  
##### <a name="localizing-the-node-name"></a>Localisation du nom de nœud  
 Lorsque Visual Studio parcourt les dossiers ProjectTemplates, il examine tous les fichiers .vstdir qu’il trouve. Un fichier .vstdir est un fichier XML qui contrôle l’apparence du type de projet dans le **nouveau projet** boîte de dialogue. Dans le fichier .vstdir, utilisez le \<LocalizedName > balise au nom de la **types de projets** nœud.  
  
 Par exemple, le fichier \CSharp\Database\TemplateIndex.vstdir contient cette balise :  
  
```  
<LocalizedName Package="{462b036f-7349-4835-9e21-bec60e989b9c}" ID="4598"/>  
```  
  
 Ce paramètre détermine l’ID de ressources et de la DLL satellite de la chaîne localisée qui nomme le nœud racine, dans ce cas, **base de données**. Le nom localisé peut contenir des caractères spéciaux qui ne sont pas disponibles pour les noms de dossier, tel que **.NET**.  
  
 Si aucun \<LocalizedName > balise est présente, le type de projet est nommé par le dossier lui-même, **SmartPhone2003**.  
  
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
  
 Si aucun \<SortOrder > balise est spécifié pour un type de projet, il apparaît dans l’ordre alphabétique suivant les types de projets qui contiennent \<SortOrder > spécifications.  
  
 Notez qu’il n’y a aucun fichier .vstdir dans Mes Documents (**Mes modèles**) dossiers. Noms de types de projet application utilisateur ne sont pas localisés et apparaissent dans l’ordre alphabétique.  
  
#### <a name="a-quick-review"></a>Un récapitulatif  
 Nous allons modifier le **nouveau projet** boîte de dialogue zone et créer un nouveau modèle de projet utilisateur.  
  
1. Ajouter un sous-dossier MyProjectNode vers le dossier \Program Files\Microsoft Visual Studio 14.0\Common7\IDE\ProjectTemplates\CSharp.  
  
2. Créer un fichier MyProject.vstdir dans le dossier MyProjectNode à l’aide de n’importe quel éditeur de texte.  
  
3. Ajoutez ces lignes au fichier .vstdir :  
  
   ```  
   <TemplateDir Version="1.0.0">  
       <SortOrder>6</SortOrder>  
   </TemplateDir>  
   ```  
  
4. Enregistrez et fermez le fichier .vstdir.  
  
5. Créer un fichier MyProject.vstemplate dans le dossier MyProjectNode à l’aide de n’importe quel éditeur de texte.  
  
6. Dans le fichier .vstemplate, ajoutez ces lignes :  
  
   ```  
   <VSTemplate Version="2.0.0" Type="Project" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
       <TemplateData>  
           <ProjectType>CSharp</ProjectType>  
       </TemplateData>  
   </VSTemplate>  
   ```  
  
7. Enregistrez le fichier de the.vstemplate et fermez l’éditeur.  
  
8. Envoyer le fichier .vstemplate dans un nouveau dossier MyProjectNode\MyProject.zip compressé.  
  
9. À partir de la fenêtre de commande Visual Studio, tapez :  
  
    ```  
    devenv /installvstemplates  
    ```  
  
   Ouvrez Visual Studio.  
  
10. Ouvrir le **nouveau projet** boîte de dialogue zone et développez le **Visual C#** nœud du projet.  
  
    ![MyProjectNode](../../extensibility/internals/media/myprojectnode.png "MyProjectNode")  
  
    **MyProjectNode** apparaît sous la forme d’un nœud enfant de Visual C# juste sous le nœud de Windows.  
  
## <a name="see-also"></a>Voir aussi  
 [Nouvelle génération de projet : Sous le capot, deuxième partie](../../extensibility/internals/new-project-generation-under-the-hood-part-two.md)