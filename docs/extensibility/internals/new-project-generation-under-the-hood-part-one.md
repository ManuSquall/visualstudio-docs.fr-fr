---
title: 'Nouvelle génération de projets : Sous le capot, première partie Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio], new project dialog
- projects [Visual Studio], new project generation
ms.assetid: 66778698-0258-467d-8b8b-c351744510eb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: aca35e85e57a07a2b411a23d81b99cff9983b9c2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707055"
---
# <a name="new-project-generation-under-the-hood-part-one"></a>Génération de nouveau projet : les rouages du système, partie 1
Avez-vous déjà pensé à la façon de créer votre propre type de projet? Vous vous demandez ce qui se passe réellement lorsque vous créez un nouveau projet? Jetons un coup d’œil sous le capot et voyons ce qui se passe vraiment.

 Il y a plusieurs tâches que Visual Studio coordonne pour vous :

- Il affiche un arbre de tous les types de projets disponibles.

- Il affiche une liste de modèles d’application pour chaque type de projet et vous permet d’en choisir un.

- Il recueille des informations de projet pour l’application, telles que le nom et le chemin du projet.

- Il transmet cette information à l’usine du projet.

- Il génère des éléments de projet et des dossiers dans la solution actuelle.

## <a name="the-new-project-dialog-box"></a>La nouvelle boîte de dialogue de projet
 Tout commence lorsque vous sélectionnez un type de projet pour un nouveau projet. Commençons par cliquer sur **New Project** sur le menu Du **fichier.** La boîte de dialogue **New Project** apparaît, ressemblant à quelque chose comme ceci:

 ![Boîte de dialogue Nouveau projet](../../extensibility/internals/media/newproject.gif "NewProject")

 Voyons cela de plus près. Les **types de projets** énumèrent les différents types de projets que vous pouvez créer. Lorsque vous sélectionnez un type de projet comme **Visual C’Windows,** vous verrez une liste de modèles d’application pour vous lancer. **Les modèles installés par Visual Studio** sont installés par Visual Studio et sont accessibles à tout utilisateur de votre ordinateur. Les nouveaux modèles que vous créez ou collectez peuvent être ajoutés à Mes Modèles et ne sont **disponibles** que pour vous.

 Lorsque vous sélectionnez un modèle comme **Windows Application**, une description du type d’application apparaît dans la boîte de dialogue; dans ce cas, **un projet pour créer une application avec une interface utilisateur Windows**.

 Au bas de la boîte de dialogue **du nouveau projet,** vous verrez plusieurs contrôles qui recueillent plus d’informations. Les contrôles que vous voyez dépendent du type de projet, mais généralement ils comprennent une boîte de texte **nom de** projet, une boîte de texte **de localisation** et le bouton De **navigation** connexe, et une boîte de texte De nom **de solution** et répertoire Create connexes pour la case à cocher **de solution.**

## <a name="populating-the-new-project-dialog-box"></a>Peupler la nouvelle boîte de dialogue de projet
 D’où provient la boîte de dialogue **du nouveau projet?** Il y a deux mécanismes à l’œuvre ici, l’un d’eux déprécié. La boîte de dialogue **du nouveau projet** combine et affiche les informations obtenues à partir des deux mécanismes.

 La méthode plus ancienne (dépréciée) utilise les entrées de registre du système et les fichiers .vsdir. Ce mécanisme s’exécute lorsque Visual Studio a ouvert. La méthode la plus nouvelle utilise des fichiers .vstemplate. Ce mécanisme s’exécute lorsque Visual Studio est parasécé, par exemple, en

```
devenv /setup
```

 or

```
devenv /installvstemplates
```

### <a name="project-types"></a>Types de projet
 La position et les noms des nœuds racines **des types de projet,** tels que **Visual CM** et **Autres langues,** sont déterminés par les entrées du registre du système. L’organisation des nœuds pour enfants, tels que **Database** et **Smart Device**, reflète la hiérarchie des dossiers qui contiennent les fichiers .vstemplate correspondants. Regardons d’abord les nœuds de racine.

#### <a name="project-type-root-nodes"></a>Nœuds de racine de type de projet
 Lorsqu’il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] est paralysé, il traverse les sous-clés de la clé de registre du système HKEY_LOCAL_MACHINE-SOFTWARE-Microsoft-VisualStudio-14.0 -NewProjectTemplates-TemplateDirs pour construire et nommer les nœuds racines de **l’arbre type projet.** Ces informations sont mises en cache pour une utilisation ultérieure. Regardez les TemplateDirs\\'FAE04EC1-301F-11D3-BF4B-00C04F79EFBCMD\\/1. Chaque entrée est un GUID VSPackage. Le nom du sous-clé (/1) est ignoré, mais sa présence indique qu’il s’agit **d’un** nœud de racine de type Projet. Un nœud de racine peut à son tour avoir plusieurs sous-clés qui contrôlent son apparence dans **l’arbre de type projet.** Regardons certains d’entre eux.

##### <a name="default"></a>(Par défaut)
 Il s’agit de l’ID de ressource de la chaîne localisée qui nomme le nœud racine. La ressource de chaîne est située dans le satellite DLL sélectionné par le GUID VSPackage.

 Dans l’exemple, le VSPackage GUID est

 FAE04EC1-301F-11D3-BF4B-00C04F79EFBC

 et l’ID de ressource (valeur par défaut) du nœud de racine (/1) est #2345

 Si vous recherchez le GUID dans la clé paquets à proximité et examinez le sous-clé SatelliteDll, vous pouvez trouver le chemin de l’assemblage qui contient la ressource de chaîne :

 \<Parcours d’installation de studio visuel>'VC’VC’VCSPackages'1033'csprojui.dll

 Pour vérifier cela, ouvrez le File Explorer et faites glisser csprojui.dll dans le répertoire Visual Studio. La table à cordes montre que la ressource #2345 a la légende **Visual C .**

##### <a name="sortpriority"></a>SortPriorité
 Cela détermine la position du nœud de racine dans l’arbre **type projet.**

 SortPriority REG_DWORD 0x0000014 (20)

 Plus le nombre de priorités est faible, plus la position dans l’arbre est élevée.

##### <a name="developeractivity"></a>DeveloperActivité
 Si cette sous-clé est présente, alors la position du nœud racine est contrôlée par la boîte de dialogue Developer Settings. Par exemple,

 DeveloperActivity REG_SZ VC #

 indique que Visual CMd sera un nœud [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] racine si Visual Studio est prêt pour le développement. Sinon, ce sera un nœud d’enfant **d’autres langues**.

##### <a name="folder"></a>Dossier
 Si cette sous-clé est présente, alors le nœud racine devient un nœud d’enfant du dossier spécifié. Une liste de dossiers possibles apparaît sous la clé

 HKEY_LOCAL_MACHINE-SOFTWARE-Microsoft-VisualStudio-11.0 -NewProjectTemplates-PseudoFolders

 Par exemple, l’entrée des projets de base de données a une clé De dossier qui correspond à l’entrée d’autres types de projets dans PseudoFolders. Ainsi, dans l’arbre **types de projet,** **projets de base de données** sera un nœud d’enfant **d’autres types de projet**.

#### <a name="project-type-child-nodes-and-vstdir-files"></a>Project Type Child Nodes et .vstdir Files
 La position des nœuds enfant dans **l’arbre type Projet** suit la hiérarchie des dossiers dans les dossiers ProjectTemplates. Pour les modèles de machines **(Visual Studio modèles installés**), l’emplacement typique est «Program Files-Microsoft Visual Studio 14.0-Common7-IDE-ProjectTemplates» et pour les modèles d’utilisateurs **(Mes modèles**), l’emplacement typique est «Mes documents -Visual Studio 14.0 -Templates-ProjectTemplates\\. Les hiérarchies de dossiers de ces deux emplacements sont fusionnées pour créer l’arbre **de type Projet.**

 Pour Visual Studio avec les paramètres du développeur C, l’arbre **de type projet** ressemble à ceci :

 ![Types de projets](../../extensibility/internals/media/projecttypes.png "ProjectTypes (projectTypes)")

 Le dossier ProjectTemplates correspondant ressemble à ceci :

 ![Modèles de projets](../../extensibility/internals/media/projecttemplates.png "ProjectTemplates (projectTemplates)")

 Lorsque la boîte de dialogue [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] du nouveau **projet** s’ouvre, traverse le dossier ProjectTemplates et recrée sa structure dans l’arbre type **Projet** avec quelques changements :

- Le nœud de racine dans l’arbre **de type projet** est déterminé par le modèle d’application.

- Le nom du nœud peut être localisé et peut contenir des caractères spéciaux.

- L’ordre de tri peut être modifié.

##### <a name="finding-the-root-node-for-a-project-type"></a>Trouver le nœud racine pour un type de projet
 Lorsque Visual Studio traverse les dossiers ProjectTemplates, il ouvre tous les fichiers .zip et extrait tous les fichiers .vstemplate. Un fichier .vstemplate utilise XML pour décrire un modèle d’application. Pour plus d’informations, voir [New Project Generation: Under the Hood, Part Two](../../extensibility/internals/new-project-generation-under-the-hood-part-two.md).

 L’étiquette \<ProjectType> détermine le type de projet pour l’application. Par exemple, le fichier 'CSharp’SmartDevice’WindowsCE'1033-WindowsCE-EmptyProject.zip contient un fichier EmptyProject.vstemplate qui a cette étiquette :

```
<ProjectType>CSharp</ProjectType>
```

 L’étiquette \<ProjectType>, et non le sous-plieur dans le dossier ProjectTemplates, détermine le nœud de racine d’une application dans l’arbre **type projet.** Dans l’exemple, les applications Windows CE apparaîtraient sous le nœud de racine **Visual C,** et même si vous devait déplacer le dossier WindowsCE vers le dossier VisualBasic, les applications Windows CE apparaissent toujours sous le nœud racine **Visual C.**

##### <a name="localizing-the-node-name"></a>Localisation du nom du nœud
 Lorsque Visual Studio traverse les dossiers ProjectTemplates, il examine tous les fichiers .vstdir qu’il trouve. Un fichier .vstdir est un fichier XML qui contrôle l’apparence du type de projet dans la boîte de dialogue **New Project.** Dans le fichier .vstdir, utilisez l’étiquette \<De> LocalizedName pour nommer le nœud de type **Projet.**

 Par exemple, le fichier 'CSharp’Database’TemplateIndex.vstdir contient cette balise :

```
<LocalizedName Package="{462b036f-7349-4835-9e21-bec60e989b9c}" ID="4598"/>
```

 Cela détermine le satellite DLL et la pièce d’identité de ressources de la chaîne localisée qui nomme le nœud racine, dans ce cas, **Base de données**. Le nom localisé peut contenir des caractères spéciaux qui ne sont pas disponibles pour les noms de dossier, tels que **.NET**.

 Si \<aucune balise De> LocalizedName n’est présente, le type de projet est nommé par le dossier lui-même, **SmartPhone2003**.

##### <a name="finding-the-sort-order-for-a-project-type"></a>Trouver l’ordre de tri pour un type de projet
 Pour déterminer le tri d’ordre du type de \<projet, les fichiers .vstdir utilisent l’étiquette De> SortOrder.

 Par exemple, le fichier 'CSharp’Windows.Windows.vstdir contient cette balise :

```
<SortOrder>5</SortOrder>
```

 Le fichier 'CSharp’Database’TemplateIndex.vstdir a une étiquette avec une plus grande valeur :

```
<SortOrder>5000</SortOrder>
```

 Plus le nombre \<dans l’étiquette SortOrder>, plus la position dans l’arbre est élevée, de sorte que le nœud **Windows** apparaît plus haut que le nœud **de base de données** dans l’arbre type **Projet.**

 Si \<aucune étiquette de> SortOrder n’est spécifiée pour un type de \<projet, elle apparaît par ordre alphabétique suivant les types de projets qui contiennent des spécifications de> De SortOrder.

 Notez qu’il n’y a pas de fichiers .vstdir dans les dossiers My Documents (**My Templates).** Les noms de type de projet d’application utilisateur ne sont pas localisés et apparaissent par ordre alphabétique.

#### <a name="a-quick-review"></a>Un examen rapide
 Modifions la boîte de dialogue **New Project** et créons un nouveau modèle de projet utilisateur.

1. Ajoutez un sous-plieur MyProjectNode au dossier 'Program Files’Microsoft Visual Studio 14.0'Common7'IDE’ProjectTemplates-CSharp.

2. Créez un fichier MyProject.vstdir dans le dossier MyProjectNode à l’aide de n’importe quel éditeur de texte.

3. Ajoutez ces lignes au fichier .vstdir :

   ```
   <TemplateDir Version="1.0.0">
       <SortOrder>6</SortOrder>
   </TemplateDir>
   ```

4. Enregistrer et fermer le fichier .vstdir.

5. Créez un fichier MyProject.vstemplate dans le dossier MyProjectNode à l’aide de n’importe quel éditeur de texte.

6. Ajoutez ces lignes au fichier .vstemplate :

   ```
   <VSTemplate Version="2.0.0" Type="Project" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
       <TemplateData>
           <ProjectType>CSharp</ProjectType>
       </TemplateData>
   </VSTemplate>
   ```

7. Enregistrer le fichier.vstemplate et fermer l’éditeur.

8. Envoyez le fichier .vstemplate à un nouveau dossier MyProjectNode.MyProject.zip compressé.

9. De la fenêtre de commande Visual Studio, tapez :

    ```
    devenv /installvstemplates
    ```

   Ouvrez Visual Studio.

10. Ouvrez la boîte de dialogue **du nouveau projet** et agrandir le nœud du projet Visual **CMD.**

    ![MyProjectNode](../../extensibility/internals/media/myprojectnode.png "MyProjectNode")

    **MyProjectNode** apparaît comme un nœud d’enfant de Visual C ' juste sous le nœud Windows.

## <a name="see-also"></a>Voir aussi
- [Génération de nouveau projet : les rouages du système, partie 2](../../extensibility/internals/new-project-generation-under-the-hood-part-two.md)
