---
title: "D&#233;pannage de r&#233;f&#233;rences rompues | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "référencer des composants, dépanner"
  - "référencer des fichiers à partir de projets"
  - "dépanner des références"
  - "projets Visual Basic, références"
  - "projets Visual C#, références"
ms.assetid: 00a9ade9-652e-40de-8ada-85f63cd183ee
caps.latest.revision: 15
caps.handback.revision: 15
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# D&#233;pannage de r&#233;f&#233;rences rompues
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Si votre application tente d'utiliser une référence rompue, le système lève une exception.  Si la première cause d'erreur reste l'impossibilité de localiser le composant référencé, une référence rompue peut, toutefois, avoir d'autres raisons.  Ces causes sont répertoriées ci\-dessous :  
  
-   Le chemin d'accès de la référence du projet est incorrect ou incomplet.  
  
-   Le fichier référencé a été supprimé.  
  
-   Le fichier référencé a été renommé.  
  
-   La connexion réseau ou l'authentification a échoué.  
  
-   La référence pointe vers un composant COM qui n'est pas installé sur l'ordinateur.  
  
 Les solutions suivantes permettent de pallier ces problèmes.  
  
> [!NOTE]
>  Les fichiers situés dans les assemblys sont référencés au moyen de chemins d'accès absolus dans le fichier projet.  Par conséquent, il est possible que les utilisateurs travaillant dans un environnement comprenant plusieurs développeurs manquent un assembly référencé dans leur environnement local.  Pour éviter ces erreurs, il est préférable dans ce cas d'ajouter des références entre projets.  Pour plus d'informations, consultez [NIB How to: Add or Remove References By Using the Add Reference Dialog Box](http://msdn.microsoft.com/fr-fr/3bd75d61-f00c-47c0-86a2-dd1f20e231c9) et [Programmation à l'aide d'assemblys](../Topic/Programming%20with%20Assemblies.md).  
  
## Le chemin d'accès de la référence est incorrect  
 Si les projets sont partagés sur différents ordinateurs, certaines références peuvent être rompues lorsqu'un composant est placé dans un répertoire différent sur chaque ordinateur.  Les références sont stockées sous le nom du fichier de composant \(par exemple, MyComponent\).  Lors de l'ajout d'une référence à un projet, l'emplacement de dossier du fichier de composant \(par exemple, C:\\MyComponents\\\) est ajouté à la propriété **ReferencePath** du projet.  
  
 À l'ouverture du projet, le système tente de localiser ces fichiers de composant référencés en effectuant une recherche dans les répertoires situés dans le chemin d'accès de la référence.  Si le projet est ouvert sur un ordinateur qui stocke le composant dans un autre répertoire, par exemple D:\\MyComponents\\, il est impossible de trouver la référence et une erreur s'affiche dans la Liste des tâches.  
  
 Pour résoudre ce problème, vous pouvez supprimer la référence rompue puis la remplacer à l'aide de la boîte de dialogue Ajouter une référence.  Une autre solution consiste à utiliser l'élément **Chemin d'accès de référence** dans les pages de propriétés du projet et de modifier les dossiers de la liste afin qu'ils pointent vers les emplacements corrects.  La propriété **Chemin d'accès de référence** est rendue persistante pour chaque utilisateur de chaque ordinateur.  Par conséquent, la modification du chemin d'accès de la référence n'affecte pas les autres utilisateurs du projet.  
  
> [!TIP]
>  Ces problèmes ne se posent pas pour les références entre projets.  Dès lors, utilisez\-les en lieu et place des références de fichier, si possible.  
  
#### Pour réparer une référence de projet rompue en corrigeant le chemin d'accès de la référence  
  
1.  Dans l'**Explorateur de solutions**, cliquez avec le bouton droit sur votre nœud de projet, puis cliquez sur **Propriétés**.  
  
2.  Le **Concepteur de projets** apparaît.  
  
3.  Si vous utilisez Visual Basic, sélectionnez la page **Références** et cliquez sur le bouton **Chemins d'accès des références**.  Dans la boîte de dialogue **Chemins d'accès des références**, entrez le chemin d'accès du dossier qui contient l'élément que vous souhaitez référencer dans le champ **Dossier**, puis cliquez sur le bouton **Ajouter un dossier**.  
  
     ou  
  
     Si vous utilisez Visual C\#, sélectionnez la page **Chemins d'accès des références**.  Dans le champ **Dossier**, entrez le chemin d'accès du dossier qui contient l'élément que vous souhaitez référencer, puis cliquez sur le bouton **Ajouter un dossier**.  
  
## Un fichier référencé a été supprimé  
 Il est possible que le fichier référencé ait été supprimé et n'existe plus sur le lecteur.  
  
#### Pour réparer une référence de projet rompue d'un fichier qui n'existe plus sur le lecteur  
  
-   Supprimez la référence.  
  
-   Si la référence existe à un autre emplacement sur l'ordinateur, lisez\-la à partir de cet emplacement.  
  
-   Pour plus d'informations, consultez [NIB How to: Add or Remove References By Using the Add Reference Dialog Box](http://msdn.microsoft.com/fr-fr/3bd75d61-f00c-47c0-86a2-dd1f20e231c9).  
  
## Un fichier référencé a été renommé  
 Il est possible que le fichier référencé ait été renommé.  
  
#### Pour réparer une référence rompue d'un fichier qui a été renommé  
  
-   Supprimez la référence, puis ajoutez une référence au nouveau nom.  
  
-   Si la référence existe à un autre emplacement sur l'ordinateur, lisez\-la à partir de cet emplacement.  Pour plus d'informations, consultez [NIB How to: Add or Remove References By Using the Add Reference Dialog Box](http://msdn.microsoft.com/fr-fr/3bd75d61-f00c-47c0-86a2-dd1f20e231c9).  
  
## La connexion réseau ou l'authentification a échoué  
 Il peut exister quantité de raisons expliquant l'inaccessibilité des fichiers : un échec de la connexion réseau ou de l'authentification, par exemple.  À chaque cause d'un problème peut être associée une solution unique ; par exemple, il est possible que vous deviez contacter l'administrateur local pour qu'il vous donne accès aux ressources requises.  Toutefois, il est toujours possible de supprimer la référence et de réparer le code qui l'utilise.  Pour plus d'informations, consultez [NIB How to: Add or Remove References By Using the Add Reference Dialog Box](http://msdn.microsoft.com/fr-fr/3bd75d61-f00c-47c0-86a2-dd1f20e231c9).  
  
## Le composant COM n'est pas installé sur l'ordinateur  
 Si un utilisateur a ajouté une référence à un composant COM et qu'un second utilisateur tente d'exécuter le code sur un ordinateur où ce composant n'est pas installé, ce second utilisateur voit s'afficher un message d'erreur indiquant que la référence est rompue.  Cette erreur peut être corrigée en installant le composant sur le second ordinateur.  Pour plus d'informations sur l'utilisation de références aux composants COM dans vos projets, consultez [COM Interoperability in .NET Framework Applications](/dotnet/visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications).  
  
## Voir aussi  
 [Introduction to the Project Designer](http://msdn.microsoft.com/fr-fr/898dd854-c98d-430c-ba1b-a913ce3c73d7)   
 [Page Références, Concepteur de projets \(Visual Basic\)](../ide/reference/references-page-project-designer-visual-basic.md)   
 [NIB How to: Add or Remove References By Using the Add Reference Dialog Box](http://msdn.microsoft.com/fr-fr/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)