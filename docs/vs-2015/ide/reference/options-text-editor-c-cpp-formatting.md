---
title: Options, Éditeur de texte, C-C++, Mise en forme | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.C/C++.Formatting.General
- VS.ToolsOptionsPages.Text_Editor.C%2fC%2b%2b.Formatting.General
dev_langs:
- C++
helpviewer_keywords:
- Text Editor Options dialog box, formatting
ms.assetid: cb6f1cbb-5305-48da-a8e8-33fd70775d46
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 5ad06dfb32c301985eb4976f6c89c7be1e0e68da
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72662342"
---
# <a name="options-text-editor-cc-formatting"></a>Options, Éditeur de texte, C/C++, Mise en forme
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Vous permet de modifier le comportement par défaut de l'Éditeur de code lorsque vous programmez en C ou C++.

 Pour accéder à cette page, dans la boîte de dialogue **Options**, dans le volet gauche, développez **Éditeur de texte**, développez **C/C++**, puis cliquez sur **Mise en forme**.

> [!NOTE]
> Il est possible que pour certains des éléments de l'interface utilisateur de Visual Studio, votre ordinateur affiche des noms ou des emplacements différents de ceux indiqués dans les instructions suivantes. L'édition de Visual Studio dont vous disposez et les paramètres que vous utilisez déterminent ces éléments. Pour plus d’informations, consultez [Personnalisation des paramètres de développement dans Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).

## <a name="cc-options"></a>Options C/C++
 **Activer les info-bulles Info Express automatique** Active ou désactive la fonctionnalité IntelliSense Info Express.

## <a name="inactive-code"></a>Code inactif
 **Afficher les blocs de code inactifs** Le code qui est inactif en raison de `#ifdef` déclarations est coloré différemment pour vous aider à l’identifier.

 **Désactiver l’opacité du code inactif** Le code inactif peut être identifié à l’aide de la couleur au lieu de la transparence.

 **Pourcentage d’opacité du code inactif** Le degré d’opacité des blocs de code inactifs peut être personnalisé.

## <a name="indentation"></a>Indentation
 **Mettre en retrait les accolades** Vous pouvez configurer la façon dont les accolades sont alignées lorsque vous appuyez sur entrée après avoir commencé un bloc de code, par exemple une fonction ou une `for` boucle. Les accolades peuvent être alignées avec le premier caractère du bloc de code ou mises en retrait.

 **Mise en retrait automatique sur l’onglet** Vous pouvez configurer ce qui se produit sur la ligne de code actuelle lorsque vous appuyez sur la touche TAB. La ligne est mise en retrait ou un onglet est inséré.

## <a name="miscellaneous"></a>Divers
 **Énumérer les commentaires dans la fenêtre Liste des tâches** L’éditeur peut analyser les fichiers Open source à la recherche de mots prédéfinis dans les commentaires. Il crée une entrée dans la fenêtre **Liste des tâches** pour tous les mots clés qu’il trouve.

 **Mettre en surbrillance les jetons correspondants** Lorsque le curseur se trouve à côté d’une accolade, l’éditeur peut mettre en surbrillance l’accolade correspondante afin que vous puissiez voir plus facilement le code qu’il contient.

## <a name="outlining"></a>mode Plan
 **Passer en mode plan** à l’ouverture des fichiers Lorsque vous placez un fichier dans l’éditeur de texte, vous pouvez activer la fonctionnalité mode plan. Pour plus d’informations, voir [Mode Plan](../../ide/outlining.md). Lorsque cette option est sélectionnée, la fonctionnalité mode Plan est activée à l’ouverture d’un fichier.

 **Mode plan automatique des blocs de #pragma région** Lorsque cette option est sélectionnée, le mode plan automatique pour les [directives de pragma](https://msdn.microsoft.com/library/9867b438-ac64-4e10-973f-c3955209873f) est activé. Cela vous permet de développer ou de réduire les blocs de région pragma en mode Plan.

 **Mode plan automatique des blocs d’instructions** Lorsque cette option est sélectionnée, le mode plan automatique est activé pour les constructions d’instruction suivantes :

- [if-else](https://msdn.microsoft.com/library/d9a1d562-8cf5-4bd4-9ba7-8ad970cd25b2)

- [Switch, instruction (C++)](https://msdn.microsoft.com/library/6c3f3ed3-5593-463c-8f4b-b33742b455c6)

- [while, instruction (C++)](https://msdn.microsoft.com/library/358dbe76-5e5e-4af5-b575-c2293c636899)

## <a name="see-also"></a>Voir aussi
 [Général, environnement, boîte de dialogue Options](../../ide/reference/general-environment-options-dialog-box.md) [avec IntelliSense](../../ide/using-intellisense.md)
