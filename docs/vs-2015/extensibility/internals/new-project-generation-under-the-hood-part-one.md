---
title: 'Nouvelle génération de projet : en coulisses, première partie | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio], new project dialog
- projects [Visual Studio], new project generation
ms.assetid: 66778698-0258-467d-8b8b-c351744510eb
caps.latest.revision: 30
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6f26c093f09cd5b7b99f00ee69a81be99c769e2e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68184137"
---
# <a name="new-project-generation-under-the-hood-part-one"></a>Nouvelle génération de projet : Rouages du système, première partie
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Avez-vous déjà pensé comment créer votre propre type de projet ? Vous vous demandez ce qui se passe quand vous créez un projet ? Jetons un coup d’œil pour voir ce qui se passe vraiment.  
  
 Visual Studio peut coordonner plusieurs tâches :  
  
- Elle affiche une arborescence de tous les types de projet disponibles.  
  
- Il affiche la liste des modèles d’application pour chaque type de projet et vous permet d’en choisir un.  
  
- Il collecte des informations sur le projet pour l’application, telles que le nom et le chemin d’accès du projet.  
  
- Il transmet ces informations à la fabrique de projets.  
  
- Il génère des éléments de projet et des dossiers dans la solution actuelle.  
  
## <a name="the-new-project-dialog-box"></a>Boîte de dialogue Nouveau projet  
 Tout commence lorsque vous sélectionnez un type de projet pour un nouveau projet. Commençons par cliquer sur **nouveau projet** dans le menu **fichier** . La boîte de dialogue **nouveau projet** s’affiche et ressemble à ce qui suit :  
  
 ![Boîte de dialogue Nouveau projet](../../extensibility/internals/media/newproject.gif "NewProject")  
  
 Examinons cela de plus près. L’arborescence **types de projets** répertorie les différents types de projets que vous pouvez créer. Lorsque vous sélectionnez un type de projet tel que **Windows Visual C#**, vous verrez une liste de modèles d’application pour vous aider à démarrer. Les **modèles Visual Studio installés** sont installés par Visual Studio et sont disponibles pour tous les utilisateurs de votre ordinateur. Les nouveaux modèles créés ou collectés peuvent être ajoutés à **Mes modèles** et ne sont disponibles que pour vous.  
  
 Lorsque vous sélectionnez un modèle comme une **application Windows**, une description du type d’application s’affiche dans la boîte de dialogue. dans ce cas, **projet pour la création d’une application avec une interface utilisateur Windows**.  
  
 En bas de la boîte de dialogue **nouveau projet** , vous verrez plusieurs contrôles qui recueillent des informations supplémentaires. Les contrôles qui s’affichent dépendent du type de projet, mais ils incluent généralement une zone de texte **nom** du projet, une zone de texte d' **emplacement** et le bouton **Parcourir** associé, ainsi qu’une zone de texte nom de la **solution** et la case à cocher **créer le répertoire pour la solution** .  
  
## <a name="populating-the-new-project-dialog-box"></a>Remplissage de la boîte de dialogue Nouveau projet  
 À partir de où la boîte de dialogue **nouveau projet** récupère-t-elle les informations ? Il existe deux mécanismes au travail, l’un d’eux étant déconseillé. La boîte de dialogue **nouveau projet** combine et affiche les informations obtenues à partir des deux mécanismes.  
  
 La méthode la plus ancienne (déconseillée) utilise des entrées du Registre système et des fichiers. vsdir. Ce mécanisme s’exécute lors de l’ouverture de Visual Studio. La méthode la plus récente utilise des fichiers. vstemplate. Ce mécanisme s’exécute quand Visual Studio est initialisé, par exemple, en exécutant  
  
```  
devenv /setup  
```  
  
 ou  
  
```  
devenv /installvstemplates  
```  
  
### <a name="project-types"></a>Types de projet  
 La position et les noms des nœuds racine des **types de projets** , tels que **Visual C#** et d' **autres langages**, sont déterminés par les entrées de Registre système. L’Organisation des nœuds enfants, tels que la **base de données** et l' **appareil intelligent**, reflète la hiérarchie des dossiers qui contiennent les fichiers. vstemplate correspondants. Examinons d’abord les nœuds racine.  
  
#### <a name="project-type-root-nodes"></a>Nœuds racines de type de projet  
 Lorsque [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] est initialisé, il parcourt les sous-clés de la clé de Registre système HKEY_LOCAL_MACHINE \software\microsoft\visualstudio\14.0\NewProjectTemplates\TemplateDirs pour générer et nommer les nœuds racines de l’arborescence des **types de projets** . Ces informations sont mises en cache pour une utilisation ultérieure. Examinez la \\ clé TemplateDirs {FAE04EC1-301F-11D3-BF4B-00C04F79EFBC} \\ /1. Chaque entrée est un GUID VSPackage. Le nom de la sous-clé (/1) est ignoré, mais sa présence indique qu’il s’agit d’un nœud racine des **types de projet** . Un nœud racine peut à son tour comporter plusieurs sous-clés qui contrôlent son apparence dans l’arborescence des **types de projets** . Examinons certaines d’entre elles.  
  
##### <a name="default"></a>(Par défaut)  
 Il s’agit de l’ID de ressource de la chaîne localisée qui nomme le nœud racine. La ressource de type chaîne se trouve dans la DLL satellite sélectionnée par le GUID du VSPackage.  
  
 Dans l’exemple, le GUID du VSPackage est  
  
 {FAE04EC1-301F-11D3-BF4B-00C04F79EFBC}  
  
 et l’ID de ressource (valeur par défaut) du nœud racine (/1) est #2345  
  
 Si vous recherchez le GUID dans la clé des packages proches et que vous examinez la sous-clé SatelliteDll, vous pouvez trouver le chemin d’accès de l’assembly qui contient la ressource de chaîne :  
  
 \<Visual Studio installation path>\VC # \VCSPackages\1033\csprojui.dll  
  
 Pour vérifier cela, ouvrez l’Explorateur de fichiers et faites glisser csprojui.dll dans le répertoire Visual Studio. La table de chaînes indique que la #2345 de ressource a la légende **Visual C#**.  
  
##### <a name="sortpriority"></a>SortPriority  
 Cela détermine la position du nœud racine dans l’arborescence des **types de projets** .  
  
 SortPriority REG_DWORD 0x00000014 (20)  
  
 Plus le nombre de priorités est faible, plus la position dans l’arborescence est élevée.  
  
##### <a name="developeractivity"></a>DeveloperActivity  
 Si cette sous-clé est présente, la position du nœud racine est contrôlée par la boîte de dialogue Paramètres du développeur. Par exemple,  
  
 DeveloperActivity REG_SZ VC #  
  
 indique que Visual C# sera un nœud racine si Visual Studio est défini pour le [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] développement. Dans le cas contraire, il s’agira d’un nœud enfant d' **autres langages**.  
  
##### <a name="folder"></a>Dossier  
 Si cette sous-clé est présente, le nœud racine devient un nœud enfant du dossier spécifié. Une liste de dossiers possibles s’affiche sous la clé  
  
 HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\VisualStudio\11.0\NewProjectTemplates\PseudoFolders  
  
 Par exemple, l’entrée projets de base de données a une clé de dossier qui correspond à l’entrée autres types de projets dans PseudoFolders. Ainsi, dans l’arborescence des **types de projets** , les **projets de base de données** seront un nœud enfant d' **autres types de projets**.  
  
#### <a name="project-type-child-nodes-and-vstdir-files"></a>Types de projet nœuds enfants et fichiers. vstdir  
 La position des nœuds enfants dans l’arborescence des **types de projets** suit la hiérarchie des dossiers dans les dossiers ProjectTemplates. Pour les modèles d’ordinateur (**modèles Visual Studio installés**), l’emplacement standard est \Program Files\Microsoft Visual Studio 14.0 \ Common7\IDE\ProjectTemplates\ et pour les modèles utilisateur (**Mes modèles**), l’emplacement standard est \Mes documents\Visual Studio 14.0 \ Templates\ProjectTemplates \\ . Les hiérarchies de dossiers de ces deux emplacements sont fusionnées pour créer l’arborescence des **types de projets** .  
  
 Pour Visual Studio avec les paramètres de développement C#, l’arborescence des **types de projets** ressemble à ceci :  
  
 ![Types de projets](../../extensibility/internals/media/projecttypes.png "ProjectTypes")  
  
 Le dossier ProjectTemplates correspondant se présente comme suit :  
  
 ![Modèles de projet](../../extensibility/internals/media/projecttemplates.png "ProjectTemplates")  
  
 Quand la boîte **de dialogue Nouveau projet** s’ouvre, [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] parcourt le dossier ProjectTemplates et recrée sa structure dans l’arborescence **types de projets** avec quelques modifications :  
  
- Le nœud racine de l’arborescence des **types de projets** est déterminé par le modèle d’application.  
  
- Le nom du nœud peut être localisé et peut contenir des caractères spéciaux.  
  
- L’ordre de tri peut être modifié.  
  
##### <a name="finding-the-root-node-for-a-project-type"></a>Recherche du nœud racine pour un type de projet  
 Lorsque Visual Studio parcourt les dossiers ProjectTemplates, il ouvre tous les fichiers. zip et extrait tous les fichiers. vstemplate. Un fichier. vstemplate utilise XML pour décrire un modèle d’application. Pour plus d’informations, consultez [nouvelle génération de projet : sous le capot, deuxième partie](../../extensibility/internals/new-project-generation-under-the-hood-part-two.md).  
  
 La \<ProjectType> balise détermine le type de projet de l’application. Par exemple, le fichier \CSharp\SmartDevice\WindowsCE\1033\WindowsCE-EmptyProject.zip contient un fichier EmptyProject. vstemplate contenant cette balise :  
  
```  
<ProjectType>CSharp</ProjectType>  
```  
  
 La \<ProjectType> balise, et non le sous-dossier du dossier ProjectTemplates, détermine le nœud racine d’une application dans l’arborescence **types de projets** . Dans l’exemple, Windows CE applications s’affichent sous le nœud racine **Visual c#** , et même si vous deviez déplacer le dossier WindowsCE vers le dossier VisualBasic, Windows ce applications apparaissent toujours sous le nœud racine **Visual c#** .  
  
##### <a name="localizing-the-node-name"></a>Localisation du nom du nœud  
 Lorsque Visual Studio parcourt les dossiers ProjectTemplates, il examine tous les fichiers. vstdir qu’il trouve. Un fichier. vstdir est un fichier XML qui contrôle l’apparence du type de projet dans la boîte de dialogue **nouveau projet** . Dans le fichier. vstdir, utilisez la \<LocalizedName> balise pour nommer le nœud **types de projets** .  
  
 Par exemple, le fichier \CSharp\Database\TemplateIndex.vstdir contient cette balise :  
  
```  
<LocalizedName Package="{462b036f-7349-4835-9e21-bec60e989b9c}" ID="4598"/>  
```  
  
 Cela détermine la DLL satellite et l’ID de ressource de la chaîne localisée qui nomme le nœud racine, dans ce cas, la **base de données**. Le nom localisé peut contenir des caractères spéciaux qui ne sont pas disponibles pour les noms de dossiers, tels que **.net**.  
  
 Si aucune \<LocalizedName> balise n’est présente, le type de projet est nommé par le dossier lui-même, **SmartPhone2003**.  
  
##### <a name="finding-the-sort-order-for-a-project-type"></a>Recherche de l’ordre de tri pour un type de projet  
 Pour déterminer l’ordre de tri du type de projet, les fichiers. vstdir utilisent la \<SortOrder> balise.  
  
 Par exemple, le fichier \CSharp\Windows\Windows.vstdir contient cette balise :  
  
```  
<SortOrder>5</SortOrder>  
```  
  
 Le fichier \CSharp\Database\TemplateIndex.vstdir a une balise avec une valeur supérieure :  
  
```  
<SortOrder>5000</SortOrder>  
```  
  
 Plus le nombre de \<SortOrder> balises est faible, plus la position dans l’arborescence est élevée, donc le nœud **Windows** apparaît plus haut que le nœud **de base de données** dans l’arborescence des **types de projets** .  
  
 Si aucune \<SortOrder> balise n’est spécifiée pour un type de projet, elle apparaît dans l’ordre alphabétique à la suite des types de projet qui contiennent des \<SortOrder> spécifications.  
  
 Notez qu’il n’y a aucun fichier. vstdir dans les dossiers Mes documents (**Mes modèles**). Les noms de types de projets d’application utilisateur ne sont pas localisés et s’affichent par ordre alphabétique.  
  
#### <a name="a-quick-review"></a>Un examen rapide  
 Modifions la boîte de dialogue **nouveau projet** et créons un nouveau modèle de projet utilisateur.  
  
1. Ajoutez un sous-dossier MyProjectNode dans le dossier \Program Files\Microsoft Visual Studio 14.0 \ Common7\IDE\ProjectTemplates\CSharp  
  
2. Créez un fichier MyProject. vstdir dans le dossier MyProjectNode à l’aide de n’importe quel éditeur de texte.  
  
3. Ajoutez ces lignes au fichier. vstdir :  
  
   ```  
   <TemplateDir Version="1.0.0">  
       <SortOrder>6</SortOrder>  
   </TemplateDir>  
   ```  
  
4. Enregistrez et fermez le fichier. vstdir.  
  
5. Créez un fichier MyProject. vstemplate dans le dossier MyProjectNode à l’aide de n’importe quel éditeur de texte.  
  
6. Ajoutez ces lignes au fichier. vstemplate :  
  
   ```  
   <VSTemplate Version="2.0.0" Type="Project" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
       <TemplateData>  
           <ProjectType>CSharp</ProjectType>  
       </TemplateData>  
   </VSTemplate>  
   ```  
  
7. Enregistrez le fichier. vstemplate et fermez l’éditeur.  
  
8. Envoyez le fichier. vstemplate à un nouveau dossier MyProjectNode\MyProject.zip compressé.  
  
9. Dans la fenêtre commande de Visual Studio, tapez :  
  
    ```  
    devenv /installvstemplates  
    ```  
  
   Ouvrez Visual Studio.  
  
10. Ouvrez la boîte de dialogue **nouveau projet** et développez le nœud de projet **Visual C#** .  
  
    ![MyProjectNode](../../extensibility/internals/media/myprojectnode.png "MyProjectNode")  
  
    **MyProjectNode** apparaît en tant que nœud enfant de Visual C# juste sous le nœud Windows.  
  
## <a name="see-also"></a>Voir aussi  
 [Nouvelle génération de projet : Rouages du système, seconde partie](../../extensibility/internals/new-project-generation-under-the-hood-part-two.md)
