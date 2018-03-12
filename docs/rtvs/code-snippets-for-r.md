---
title: Extraits de code avec les Outils R pour Visual Studio | Microsoft Docs
description: "Les extraits de code pour R dans Visual Studio fournissent des raccourcis pour insérer rapidement des blocs de code de longueur arbitraire, ce qui vous évite de retaper du code similaire plusieurs fois de suite."
ms.custom: 
ms.date: 01/24/2018
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-r
dev_langs:
- R
ms.tgt_pltfrm: 
ms.topic: article
author: kraigb
ms.author: kraigb
manager: ghogen
ms.workload:
- data-science
ms.openlocfilehash: d8628b2712c52aae614223b702344bb0b548e306
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/09/2018
---
# <a name="code-snippets"></a>Extraits de code

Les extraits de code dans Visual Studio fournissent des raccourcis pour insérer rapidement des blocs de code de longueur arbitraire, ce qui vous évite de retaper du code similaire plusieurs fois de suite. Les Outils R pour Visual Studio (RTVS) ajoutent des dizaines d’extraits de code R utiles à la collection de Visual Studio.

Pour insérer un extrait de code, tapez le nom abrégé de l’extrait de code (IntelliSense est fourni), puis appuyez sur Tab pour l’insérer.

Voici quelques exemples simples :

- tapez `=`, puis appuyez sur Tab : RTVS le convertit en opérateur d’assignation `<-`.
- tapez `>`, puis appuyez sur Tab : RTVS le convertit en opérateur de barre verticale `%>%`.

Les extraits de code peuvent apporter bien plus que la saisie semi-automatique de caractères. Un extrait de code qui permet de lire un fichier CSV avec la fonction `read.csv`, par exemple, peut vous éviter d’avoir à mémoriser les noms ou paramètres :

![Animation de l’utilisation d’un extrait de code pour insérer un appel dans read.csv](media/code-snippet-expansion.gif)

Dans ce cas, quand vous tapez `readc`, IntelliSense affiche une liste de saisie semi-automatique. En sélectionnant cette saisie semi-automatique dans la liste déroulante et en appuyant sur Tab, vous sélectionnez `readc` et, en appuyant de nouveau sur Tab, vous développez l’extrait de code. (Pour cette raison, le développement de l’extrait de code est souvent évoqué comme « tapez l’extrait de code et appuyez deux fois sur Tab »). Dans la plupart des cas, le premier appui sur Tab effectue la sélection IntelliSense et le deuxième appui déclenche le développement.

Pour voir tous les extraits de code disponibles, ouvrez la boîte de dialogue **Outils > Gestionnaire des extraits de Code...** (Ctrl+K,B) et sélectionnez **R** pour **Langage**. Développez les groupes, puis sélectionnez les extraits de code individuels pour afficher une description et le texte de raccourci :

![Boîte de dialogue Extraits de code pour R](media/code-snippet-dialog.png)

Pour créer des extraits de code personnalisés, suivez les instructions de [Procédure pas à pas : création d’un extrait de code](../ide/walkthrough-creating-a-code-snippet.md). En fin de compte, un extrait de code est un simple fichier XML. Par exemple, le code suivant est l’extrait de code pour l’opération de barre verticale (raccourci `>`) :

```xml
<?xml version="1.0" encoding="utf-8" ?>
<CodeSnippets  xmlns="http://schemas.microsoft.com/VisualStudio/2005/CodeSnippet">
  <CodeSnippet Format="1.0.0">
    <Header>
      <Title>Dplyr pipe</Title>
      <Shortcut>&gt;</Shortcut>
      <Description>Code snippet for '%&gt;%' operator</Description>
      <Author>Microsoft Corporation</Author>
      <SnippetTypes>
        <SnippetType>Expansion</SnippetType>
       </SnippetTypes>
    </Header>
    <Snippet>
      <Code Language="R">
        <![CDATA[ %>% $end$]]>
      </Code>
    </Snippet>
  </CodeSnippet>
</CodeSnippets>
```

Les fichiers XML de tous les extraits de code sont installés avec RTVS. Le champ **Emplacement** du **Gestionnaire des extraits de code** fournit le chemin. Vous pouvez également les trouver dans le code source RTVS sur GitHub sous [src/Package/Impl/Snippets](https://github.com/Microsoft/RTVS/tree/master/src/Package/Impl/Snippets).
