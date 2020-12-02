---
title: Visual Basic IntelliSense
description: Découvrez comment utiliser les fonctionnalités IntelliSense offertes par l’éditeur de code source Visual Basic.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.Basic.IntelliSense
helpviewer_keywords:
- IntelliSense [Visual Basic]
- IntelliSense [Visual Studio], Visual Basic
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 70cdcf9eb6d741fc579ce555ce0bfa3cdea0d774
ms.sourcegitcommit: df6ba39a62eae387e29f89388be9e3ee5ceff69c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2020
ms.locfileid: "96478820"
---
# <a name="intellisense-for-visual-basic-code-files"></a>IntelliSense pour les fichiers de code Visual Basic

L’éditeur de code source de Visual Basic propose les fonctionnalités IntelliSense suivantes :

## <a name="syntax-tips"></a>Conseils de syntaxe

Les conseils syntaxiques affichent la syntaxe de l’instruction que vous tapez. Cela est utile pour les instructions telles que [Declare](/dotnet/visual-basic/language-reference/statements/declare-statement).

## <a name="automatic-completion"></a>Saisie semi-automatique

- Saisie semi-automatique de divers mots clés

     Par exemple, si vous tapez `goto` suivi d’un espace, IntelliSense affiche une liste des étiquettes définies dans un menu déroulant. Les autres mots clés pris en charge sont `Exit`, `Implements`, `Option` et `Declare`.

- Saisie semi-automatique pour `Enum` et`Boolean`

    Quand une instruction fait référence à un membre d’une énumération, IntelliSense affiche la liste des membres d’`Enum`. Quand une instruction fait référence à un `Boolean`, IntelliSense affiche un menu déroulant contenant les valeurs True et False.

Pour désactiver par défaut la saisie semi-automatique, désélectionnez l’option **Répertorier automatiquement les membres** dans la page de propriétés **Général** du dossier **Visual Basic**.

Vous pouvez appeler manuellement la saisie semi-automatique en appelant liste des membres, compléter le mot ou **ALT** + **droite**. Pour plus d’informations, consultez [Utiliser IntelliSense](../ide/using-intellisense.md).

## <a name="intellisense-in-zone"></a>IntelliSense par zone

IntelliSense par zone aide les développeurs Visual Basic qui doivent déployer leurs applications via [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] et sont contraints à des paramètres de confiance partielle. Cette fonctionnalité :

- vous permet de choisir les autorisations avec lesquelles l’application s’exécutera ;

- affiche les API dans la Zone choisie comme disponibles dans la Liste des membres, et les API nécessitant des autorisations supplémentaires comme non disponibles.

Pour plus d’informations, consultez [Sécurité d’accès du code pour les applications ClickOnce](../deployment/code-access-security-for-clickonce-applications.md).

## <a name="filtered-completion-lists"></a>Listes de saisie semi-automatique filtrées

En Visual Basic, les listes de saisie semi-automatique IntelliSense ont deux contrôles Onglet situés en bas de la liste. L’onglet **Commun**, qui est sélectionné par défaut, affiche les éléments qui sont utilisés le plus souvent pour compléter l’instruction que vous écrivez. L’onglet **Tout** affiche tous les éléments qui sont disponibles pour la saisie semi-automatique, notamment ceux qui figurent sous l’onglet **Commun**.

## <a name="see-also"></a>Voir aussi

- [Utilisez IntelliSense](../ide/using-intellisense.md)
