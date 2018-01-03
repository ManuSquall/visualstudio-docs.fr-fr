---
title: "Atteindre la définition et Aperçu de la définition | Microsoft Docs"
ms.custom: 
ms.date: 10/04/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- code editor, go to definition
- code editor, peek definition
- go to definition
- peek definition
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: db67f01ff2a58ee856e4588df8770fc4edef8ca2
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="go-to-definition-and-peek-definition"></a>Atteindre la définition et Aperçu de la définition  
Les fonctionnalités Atteindre la définition et Aperçu de la définition vous permettent d’afficher rapidement la définition d’un type ou d’un membre.

## <a name="go-to-definition"></a>Atteindre la définition  
La fonctionnalité Atteindre la définition accède à la source d’un type ou d’un membre et affiche le résultat dans un nouvel onglet. Si vous utilisez le clavier, placez le curseur texte dans le nom du symbole, puis appuyez sur **F12**. Si vous utilisez la souris, sélectionnez **Atteindre la définition** dans le menu contextuel ou utilisez la fonctionnalité **Ctrl+clic** décrite ci-dessous.  

### <a name="ctrl-click-go-to-definition"></a>Atteindre la définition avec Ctrl+clic  
Visual Studio 2017 version 15.4 offre aux utilisateurs de souris un moyen plus simple d’accéder rapidement à la fonctionnalité Atteindre la définition. Vous pouvez cliquer sur les symboles quand vous appuyez sur **Ctrl** et que vous pointez sur le type ou le membre. Pour accéder rapidement à la définition d’un symbole, appuyez sur la touche **Ctrl**, puis cliquez sur le symbole. C’est aussi simple que cela !

![Animation de l’accès à la définition avec un clic de souris](../ide/media/click_gotodef.gif)

Vous pouvez changer la touche de modification pour activer **Atteindre la définition** avec un clic de souris. Pour cela, accédez à **Outils**, **Options**, **Éditeur de texte**, **Général**, puis sélectionnez **Alt** ou **Ctrl+Alt** dans la liste déroulante **Utiliser la touche de modification**. Vous pouvez également désactiver **Atteindre la définition** avec un clic de souris en décochant la case **Activer le clic de souris pour exécuter Atteindre la définition**.  

![Activation du clic de souris pour la fonctionnalité Atteindre la définition](../ide/media/editor_options_mouse_click_gotodef.png)  

## <a name="peek-definition"></a>Aperçu de définition
La fonctionnalité Aperçu de la définition vous permet d’afficher un aperçu de la définition d’un type sans avoir à quitter votre emplacement actuel dans l’éditeur. Si vous utilisez le clavier, placez le curseur texte dans le nom du type ou du membre, puis appuyez sur **Alt+F12**. Si vous utilisez la souris, sélectionnez **Aperçu de la définition** dans le menu contextuel. Visual Studio 2017 version 15.4 ou ultérieure offre aux utilisateurs de souris un nouveau moyen d’accéder à l’aperçu d’une définition. Tout d’abord, accédez à **Outils**, **Options**, **Éditeur de texte**, **Général**. Sélectionnez l’option **Ouvrir la définition dans l’aperçu** et cliquez sur **OK** pour fermer la boîte de dialogue **Options**.  

![Activation de l’option Aperçu de la définition avec un clic de souris](../ide/media/editor_options_peek_view.png)  

Ensuite, appuyez sur **Ctrl** (ou sur la touche de modification sélectionnée dans **Options**), puis cliquez sur le type ou le membre.  

![Animation de l’option Aperçu de la définition](../ide/media/peek_definition.gif)

Si vous affichez un aperçu d’une autre définition à partir de la fenêtre contextuelle, vous commencerez un chemin de fil d’Ariane que vous pourrez parcourir à l’aide des cercles et des flèches qui apparaîtront au-dessus de la fenêtre contextuelle.  

Pour plus d’informations, consultez [Guide pratique pour afficher et modifier le code avec l’Aperçu de définition (Alt + F12)](how-to-view-and-edit-code-by-using-peek-definition-alt-plus-f12.md).  

## <a name="see-also"></a>Voir aussi  
[Navigation dans le code](../ide/navigating-code.md)  
[Guide pratique pour afficher et modifier le code avec l’Aperçu de définition (Alt + F12)](how-to-view-and-edit-code-by-using-peek-definition-alt-plus-f12.md)  
