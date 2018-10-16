---
title: Dépannage de références rompues | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Visual C# projects, references
- Visual Basic projects, references
- troubleshooting references
- referencing files from projects
- referencing components, troubleshooting
ms.assetid: 00a9ade9-652e-40de-8ada-85f63cd183ee
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 08cf57bb90ba85df8a818da92cfd5615c62c3468
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49292940"
---
# <a name="troubleshooting-broken-references"></a>Dépannage de références rompues
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Si votre application tente d’utiliser une référence rompue, une erreur d’exception est générée. Si la première cause d’erreur est l’impossibilité de localiser le composant référencé, il existe toutefois plusieurs situations dans lesquelles une référence peut être considérée comme rompue. Ces situations sont répertoriées dans la liste suivante :  
  
-   Le chemin de la référence du projet est incorrect ou incomplet.  
  
-   Le fichier référencé a été supprimé.  
  
-   Le fichier référencé a été renommé.  
  
-   La connexion réseau ou l’authentification a échoué.  
  
-   La référence pointe vers un composant COM qui n’est pas installé sur l’ordinateur.  
  
 Les solutions suivantes permettent de résoudre ces problèmes.  
  
> [!NOTE]
>  Les fichiers situés dans les assemblys sont référencés à l’aide de chemins absolus dans le fichier projet. Par conséquent, il est possible qu’un assembly référencé dans l’environnement local d’utilisateurs qui travaillent dans un environnement comprenant plusieurs développeurs soit manquant. Pour éviter ces erreurs, il est préférable, dans ce cas, d’ajouter des références entre projets. Pour plus d’informations, consultez [NIB Comment : ajouter ou supprimer des références à l’aide de la boîte de dialogue Ajouter une référence](http://msdn.microsoft.com/en-us/3bd75d61-f00c-47c0-86a2-dd1f20e231c9) et [Programmation à l’aide d’assemblys](http://msdn.microsoft.com/library/25918b15-701d-42c7-95fc-c290d08648d6).  
  
## <a name="reference-path-is-incorrect"></a>Le chemin de la référence est incorrect  
 Si les projets sont partagés sur différents ordinateurs, certaines références peuvent être introuvables quand un composant se trouve dans un répertoire différent sur chaque ordinateur. Les références sont stockées sous le nom du fichier du composant (par exemple, MyComponent). Lors de l’ajout d’une référence à un projet, l’emplacement de dossier du fichier de composant (par exemple, C:\MyComponents\\) est ajouté à la propriété de projet **ReferencePath**.  
  
 À son ouverture, le projet tente de localiser ces fichiers de composant référencés en effectuant une recherche dans les répertoires situés dans le chemin de la référence. S’il est ouvert sur un ordinateur qui stocke le composant dans un autre répertoire, par exemple D:\MyComponents\\, la référence est introuvable et une erreur s’affiche dans la liste des tâches.  
  
 Pour résoudre ce problème, vous pouvez supprimer la référence rompue, puis la remplacer à l’aide de la boîte de dialogue Ajouter une référence. Une autre solution consiste à utiliser l’élément **Chemins d’accès de références** dans les pages de propriétés du projet et à modifier les dossiers de la liste afin qu’ils pointent vers les emplacements corrects. La propriété **Chemin d’accès de référence** est rendue persistante pour chaque utilisateur de chaque ordinateur. Par conséquent, la modification du chemin de votre référence n’affecte pas les autres utilisateurs du projet.  
  
> [!TIP]
>  Ces problèmes ne se posent pas pour les références entre projets. Par conséquent, utilisez-les plutôt que les références de fichier, si vous le pouvez.  
  
#### <a name="to-fix-a-broken-project-reference-by-correcting-the-reference-path"></a>Pour réparer une référence de projet rompue en corrigeant son chemin  
  
1.  Dans l’**Explorateur de solutions**, cliquez avec le bouton droit sur le nœud de votre projet, puis cliquez sur **Propriétés**.  
  
2.  Le **Concepteur de projet** s’affiche.  
  
3.  Si vous utilisez Visual Basic, sélectionnez la page **Références**, puis cliquez sur le bouton **Chemins d’accès des références**. Dans la boîte de dialogue **Chemins d’accès des références**, tapez le chemin du dossier contenant l’élément que vous voulez référencer dans le champ **Dossier**, puis cliquez sur le bouton **Ajouter un dossier**.  
  
     - ou -  
  
     Si vous utilisez Visual C#, sélectionnez la page **Chemins d’accès des références**. Dans le champ **Dossier**, tapez le chemin du dossier contenant l’élément que vous voulez référencer, puis cliquez sur bouton **Ajouter un dossier**.  
  
## <a name="referenced-file-has-been-deleted"></a>Un fichier référencé a été supprimé  
 Il est possible que le fichier référencé ait été supprimé et n’existe plus sur le lecteur.  
  
#### <a name="to-fix-a-broken-project-reference-for-a-file-that-no-longer-exists-on-your-drive"></a>Pour réparer une référence de projet rompue pour un fichier qui n’existe plus sur le lecteur  
  
-   Supprimez la référence.  
  
-   Si la référence existe dans un autre emplacement sur votre ordinateur, lisez-la à partir de cet emplacement.  
  
-   Pour plus d’informations, consultez [NIB Comment : ajouter ou supprimer des références à l’aide de la boîte de dialogue Ajouter une référence](http://msdn.microsoft.com/en-us/3bd75d61-f00c-47c0-86a2-dd1f20e231c9).  
  
## <a name="referenced-file-has-been-renamed"></a>Un fichier référencé a été renommé  
 Il est possible que le fichier référencé ait été renommé.  
  
#### <a name="to-fix-a-broken-reference-for-a-file-that-has-been-renamed"></a>Pour réparer une référence rompue d’un fichier qui a été renommé  
  
-   Supprimez la référence, puis ajoutez une référence au fichier renommé.  
  
-   Si la référence existe dans un autre emplacement sur votre ordinateur, vous devez la lire à partir de cet emplacement. Pour plus d’informations, consultez [NIB Comment : ajouter ou supprimer des références à l’aide de la boîte de dialogue Ajouter une référence](http://msdn.microsoft.com/en-us/3bd75d61-f00c-47c0-86a2-dd1f20e231c9).  
  
## <a name="network-connection-or-authentication-has-failed"></a>La connexion réseau ou l’authentification a échoué  
 Il peut exister quantité de raisons expliquant l’inaccessibilité des fichiers : un échec de la connexion réseau ou de l’authentification, par exemple. À chaque cause d’un problème peut être associée une solution unique ; par exemple, vous devrez peut-être contacter l’administrateur local pour qu’il vous donne accès aux ressources nécessaires. Toutefois, il est toujours possible de supprimer la référence et de réparer le code qui l’utilise. Pour plus d’informations, consultez [NIB Comment : ajouter ou supprimer des références à l’aide de la boîte de dialogue Ajouter une référence](http://msdn.microsoft.com/en-us/3bd75d61-f00c-47c0-86a2-dd1f20e231c9).  
  
## <a name="com-component-is-not-installed-on-computer"></a>Le composant COM n’est pas installé sur l’ordinateur  
 Si un utilisateur a ajouté une référence à un composant COM et qu’un second utilisateur tente d’exécuter le code sur un ordinateur sur lequel ce composant n’est pas installé, ce second utilisateur voit s’afficher un message d’erreur indiquant que la référence est rompue. Cette erreur peut être corrigée en installant le composant sur le second ordinateur. Pour plus d’informations sur l’utilisation de références aux composants COM dans vos projets, consultez [Interopérabilité COM dans les applications .NET Framework](http://msdn.microsoft.com/library/f5a72143-c268-4dff-a019-974ad940e17d).  
  
## <a name="see-also"></a>Voir aussi  
 [Introduction au Concepteur de projets](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7)   
 [Page Références, Concepteur de projet (Visual Basic)](../ide/reference/references-page-project-designer-visual-basic.md)   
 [NIB Comment : ajouter ou supprimer des références à l’aide de la boîte de dialogue Ajouter une référence](http://msdn.microsoft.com/en-us/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)



