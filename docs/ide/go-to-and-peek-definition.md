---
title: Affichage des définitions de type
ms.date: 01/10/2018
ms.topic: conceptual
helpviewer_keywords:
- code editor, view definition
- go to definition
- peek definition
- type definition [Visual Studio]
- member definition [Visual Studio]
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3ef13b959d4e106b451ea0cfb336835059667ce4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75592072"
---
# <a name="view-type-and-member-definitions"></a>Afficher les définitions de type et de membre

Les développeurs doivent souvent afficher les définitions du code source pour les types ou membres de classe qu’ils utilisent dans leur code. Dans Visual Studio, les fonctionnalités **Atteindre la définition** et **Aperçu de la définition** vous permettent d’afficher rapidement la définition d’un type ou d’un membre. Si le code source n’est pas disponible, les métadonnées sont affichées à la place.

## <a name="go-to-definition"></a>Atteindre la définition

La fonctionnalité **atteindre la définition** permet d’accéder à la source d’un type ou d’un membre et d’ouvrir le résultat dans un nouvel onglet. Si vous êtes un utilisateur du clavier, placez le curseur de texte à l’intérieur du nom du symbole et appuyez sur **F12**. Si vous préférez utiliser la souris, sélectionnez **Atteindre la définition** dans le menu contextuel (clic droit) ou utilisez la fonctionnalité **Ctrl+clic** décrite dans la section suivante.

### <a name="ctrl-click-go-to-definition"></a>Atteindre la définition avec Ctrl+clic

**CTRL** + **cliquez sur** le raccourci permettant aux utilisateurs de la souris d’accéder rapidement **à atteindre la définition**. Vous pouvez cliquer sur les symboles quand vous appuyez sur **Ctrl** et que vous pointez sur le type ou le membre. Pour accéder rapidement à la définition d’un symbole, appuyez sur la touche **Ctrl**, puis cliquez sur le symbole. C’est aussi simple que cela !

![Animation de l’accès à la définition avec un clic de souris](../ide/media/click_gotodef.gif)

Vous pouvez modifier la touche de modification pour **accéder à la définition** en cliquant sur **Outils**  >  **options**  >  **éditeur de texte**  >  **général**, puis en sélectionnant **ALT** ou **CTRL** + **ALT** dans la liste déroulante **utiliser la touche de modification** . Vous pouvez également désactiver **Atteindre la définition** avec un clic de souris en décochant la case **Activer le clic de souris pour exécuter Atteindre la définition**.

![Activation du clic de souris pour la fonctionnalité Atteindre la définition](../ide/media/editor_options_mouse_click_gotodef.png)

## <a name="peek-definition"></a>Aperçu de la définition

La fonctionnalité **Aperçu de la définition** vous permet d’afficher un aperçu de la définition d’un type sans avoir à quitter votre emplacement actuel dans l’éditeur. Si vous utilisez le clavier, placez le curseur texte dans le nom du type ou du membre, puis appuyez sur **Alt+F12**. Si vous préférez utiliser la souris, sélectionnez **Aperçu de la définition** dans le menu contextuel (clic droit).

Pour activer la fonctionnalité **CTRL +** + **clic** , accédez à **Outils**  >  **options**  >  **éditeur de texte**  >  **général**. Sélectionnez l’option **Ouvrir la définition dans l’aperçu** et cliquez sur **OK** pour fermer la boîte de dialogue **Options**.

![Activation de l’option Aperçu de la définition avec un clic de souris](../ide/media/editor_options_peek_view.png)

Ensuite, appuyez sur **Ctrl** (ou sur la touche de modification sélectionnée dans **Options**), puis cliquez sur le type ou le membre.

![Animation de l’option Aperçu de la définition](../ide/media/peek_definition.gif)

Si vous affichez un aperçu d’une autre définition à partir de la fenêtre contextuelle, vous commencez un chemin de navigation que vous pouvez parcourir à l’aide des cercles et des flèches qui apparaissent au-dessus de la fenêtre contextuelle.

Pour plus d’informations, consultez [Guide pratique pour afficher et modifier le code avec l’Aperçu de définition (Alt+F12)](how-to-view-and-edit-code-by-using-peek-definition-alt-plus-f12.md).

## <a name="view-metadata-as-source-code-c"></a>Afficher les métadonnées en tant que code source (C#)

Quand vous visualisez la définition de types C# ou de membres dont le code source n’est pas disponible, leurs métadonnées sont affichées à la place. Vous pouvez afficher les déclarations des types et des membres, mais pas leurs implémentations.

Quand vous exécutez la commande **Atteindre la définition** ou **Aperçu de définition** pour un élément dont le code source n’est pas disponible, un document à onglets qui contient une vue des métadonnées de cet élément affichées en tant que code source apparaissent dans l’éditeur de code. Le nom du type, suivi de **[à partir des métadonnées]**, apparaît sur l’onglet du document.

Par exemple, si vous exécutez la commande **Atteindre la définition** pour <xref:System.Console>, les métadonnées de <xref:System.Console> apparaissent dans l’éditeur de code en tant que code source C#. Le code ressemble à sa déclaration, mais ne montre pas d’implémentation.

![Métadonnées en tant que source](../ide/media/metadatasource.png)

> [!NOTE]
> Quand vous essayez d’exécuter la commande **Atteindre la définition** ou **Aperçu de définition** pour des types ou des membres marqués comme internes, Visual Studio n’affiche pas leurs métadonnées en tant que code source, que l’assembly de référence soit ou non un assembly Friend.

### <a name="view-decompiled-source-definitions-instead-of-metadata-c"></a>Afficher les définitions de source décompilées au lieu de métadonnées (C#)

Vous pouvez définir une option pour afficher le code source décompilé quand vous visualisez la définition d’un type C# ou d’un membre dont le code source n’est pas disponible. Pour activer cette fonctionnalité, choisissez **Outils**  >  **options** dans la barre de menus. Ensuite, développez **éditeur de texte**  >  **C#**  >  **avancé**, puis sélectionnez **activer la navigation vers les sources décompilées**.

![Affichage d’une définition décompilée](media/go-to-definition-decompiled-sources.png)

> [!NOTE]
> Visual Studio reconstruit les corps de méthode à l’aide de la décompilation ILSpy. La première fois que vous accédez à cette fonctionnalité, vous devez accepter une clause d’exclusion de responsabilité concernant les lois sur les licences logicielles, les droits d’auteur et les marques commerciales.

## <a name="see-also"></a>Voir aussi

- [Naviguer dans le code](../ide/navigating-code.md)
- [Comment : afficher et modifier le code à l’aide de l’aperçu de définition (ALT + F12)](how-to-view-and-edit-code-by-using-peek-definition-alt-plus-f12.md)
