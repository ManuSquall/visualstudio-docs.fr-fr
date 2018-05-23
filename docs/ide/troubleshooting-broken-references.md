---
title: Dépanner des références rompues
ms.date: 03/21/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: troubleshooting
helpviewer_keywords:
- C# projects, references
- Visual Basic projects, references
- troubleshooting references
- referencing files from projects
- referencing components, troubleshooting
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3c1879b67558cb57fba7bc462e4c7df03fb5efc8
ms.sourcegitcommit: 04a717340b4ab4efc82945fbb25dfe58add2ee4c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2018
---
# <a name="troubleshoot-broken-references"></a>Dépanner des références rompues

Si votre application tente d’utiliser une référence rompue, une erreur d’exception est générée. Si la première cause d’erreur est l’impossibilité de localiser le composant référencé, il existe toutefois plusieurs situations dans lesquelles une référence peut être considérée comme rompue. Ces situations sont répertoriées dans la liste suivante :

- Le chemin de la référence du projet est incorrect ou incomplet.

- Le fichier référencé a été supprimé.

- Le fichier référencé a été renommé.

- La connexion réseau ou l’authentification a échoué.

- La référence pointe vers un composant COM qui n’est pas installé sur l’ordinateur.

Les solutions suivantes permettent de résoudre ces problèmes.

> [!NOTE]
> Les fichiers situés dans les assemblys sont référencés à l’aide de chemins absolus dans le fichier projet. Par conséquent, il est possible qu’un assembly référencé dans l’environnement local d’utilisateurs qui travaillent dans un environnement comprenant plusieurs développeurs soit manquant. Pour éviter ces erreurs, il est préférable, dans ce cas, d’ajouter des références entre projets. Pour plus d’informations, consultez [Programmation à l’aide d’assemblys](/dotnet/framework/app-domains/programming-with-assemblies).

## <a name="reference-path-is-incorrect"></a>Le chemin de la référence est incorrect

Si les projets sont partagés sur différents ordinateurs, certaines références peuvent être introuvables quand un composant se trouve dans un répertoire différent sur chaque ordinateur. Les références sont stockées sous le nom du fichier du composant (par exemple, *MyComponent*). Lors de l’ajout d’une référence à un projet, l’emplacement de dossier du fichier de composant (par exemple, *C:\MyComponents*) est ajouté à la propriété de projet **ReferencePath**.

À son ouverture, le projet tente de localiser ces fichiers de composant référencés en effectuant une recherche dans les répertoires situés dans le chemin de la référence. S’il est ouvert sur un ordinateur qui stocke le composant dans un autre répertoire, par exemple *D:\MyComponents*, la référence est introuvable et une erreur s’affiche dans la **Liste des tâches**.

Pour résoudre ce problème, vous pouvez supprimer la référence rompue, puis la remplacer à l’aide de la boîte de dialogue **Ajouter une référence**. Une autre solution consiste à utiliser l’élément **Chemins d’accès de références** dans les pages de propriétés du projet et à modifier les dossiers de la liste afin qu’ils pointent vers les emplacements corrects. La propriété **Chemin d’accès de référence** est rendue persistante pour chaque utilisateur de chaque ordinateur. Par conséquent, la modification du chemin de votre référence n’affecte pas les autres utilisateurs du projet.

> [!TIP]
> Ces problèmes ne se posent pas pour les références entre projets. Par conséquent, utilisez-les plutôt que les références de fichier, si vous le pouvez.

### <a name="to-fix-a-broken-project-reference-by-correcting-the-reference-path"></a>Pour réparer une référence de projet rompue en corrigeant son chemin

1. Dans l’**Explorateur de solutions**, cliquez avec le bouton droit sur le nœud de votre projet, puis cliquez sur **Propriétés**.

   Le **Concepteur de projet** s’affiche.

1. Si vous utilisez Visual Basic, sélectionnez la page **Références**, puis cliquez sur le bouton **Chemins d’accès des références**. Dans la boîte de dialogue **Chemins d’accès des références**, tapez le chemin du dossier contenant l’élément que vous voulez référencer dans le champ **Dossier**, puis cliquez sur le bouton **Ajouter un dossier**.

    Si vous utilisez C#, sélectionnez la page **Chemins d’accès des références**. Dans le champ **Dossier**, tapez le chemin du dossier contenant l’élément que vous voulez référencer, puis cliquez sur bouton **Ajouter un dossier**.

## <a name="referenced-file-has-been-deleted"></a>Le fichier référencé a été supprimé

Il est possible que le fichier référencé ait été supprimé et n’existe plus sur le lecteur.

### <a name="to-fix-a-broken-project-reference-for-a-file-that-no-longer-exists-on-your-drive"></a>Pour réparer une référence de projet rompue pour un fichier qui n’existe plus sur le lecteur

- Supprimez la référence.

- Si la référence existe dans un autre emplacement sur votre ordinateur, lisez-la à partir de cet emplacement.

## <a name="referenced-file-has-been-renamed"></a>Le fichier référencé a été renommé

Il est possible que le fichier référencé ait été renommé.

### <a name="to-fix-a-broken-reference-for-a-file-that-has-been-renamed"></a>Pour réparer une référence rompue d’un fichier qui a été renommé

- Supprimez la référence, puis ajoutez une référence au fichier renommé.

- Si la référence existe dans un autre emplacement sur votre ordinateur, vous devez la lire à partir de cet emplacement.

## <a name="network-connection-or-authentication-has-failed"></a>La connexion réseau ou l’authentification a échoué

Il peut exister quantité de raisons expliquant l’inaccessibilité des fichiers : un échec de la connexion réseau ou de l’authentification, par exemple. À chaque cause d’un problème peut être associée une solution unique ; par exemple, vous devrez peut-être contacter l’administrateur local pour qu’il vous donne accès aux ressources nécessaires. Toutefois, il est toujours possible de supprimer la référence et de réparer le code qui l’utilise.

## <a name="com-component-is-not-installed-on-computer"></a>Le composant COM n’est pas installé sur l’ordinateur

Si un utilisateur a ajouté une référence à un composant COM et qu’un second utilisateur tente d’exécuter le code sur un ordinateur sur lequel ce composant n’est pas installé, ce second utilisateur voit s’afficher un message d’erreur indiquant que la référence est rompue. Cette erreur peut être corrigée en installant le composant sur le second ordinateur. Pour plus d’informations sur l’utilisation de références aux composants COM dans vos projets, consultez [Interopérabilité COM dans les applications .NET Framework](/dotnet/visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications).

## <a name="see-also"></a>Voir aussi

- [Page Références, Concepteur de projets (Visual Basic)](../ide/reference/references-page-project-designer-visual-basic.md)