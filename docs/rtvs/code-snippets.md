---
title: "Extraits de code avec les Outils R pour Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 4/28/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-r
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 90bf4f87-e276-40cd-bc17-3dfb47ef1870
caps.latest.revision: 1
author: kraigb
ms.author: kraigb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: 7a873df77756e5a957d327049566c8e0db1f3a8a
ms.openlocfilehash: 033a06b276b8a31e6c69b0eff68ee3f76dda1042
ms.contentlocale: fr-fr
ms.lasthandoff: 05/12/2017

---

# <a name="code-snippets"></a>Extraits de code

Les extraits de code dans Visual Studio fournissent des raccourcis pour insérer rapidement des blocs de code de longueur arbitraire, ce qui vous évite de retaper du code similaire plusieurs fois de suite. Les Outils R pour Visual Studio (RTVS) ajoutent des dizaines d’extraits de code R utiles à la collection de Visual Studio.

Pour insérer un extrait de code, tapez le nom abrégé de l’extrait de code (IntelliSense est fourni), puis appuyez sur Tab pour l’insérer.

Voici quelques exemples simples :

- tapez `=`, puis appuyez sur Tab : RTVS le convertit en opérateur d’assignation `<-`.
- tapez `>`, puis appuyez sur Tab : RTVS le convertit en opérateur de barre verticale `%>%`.

Les extraits de code peuvent apporter bien plus que la saisie semi-automatique de caractères. Par exemple, ils peuvent vous éviter d’avoir à mémoriser les noms de paramètres dans l’appel de fonction complexes, comme cet extrait de code qui permet de lire un fichier CSV avec la fonction `read.csv` :

![Animation de l’utilisation d’un extrait de code pour insérer un appel dans read.csv](~/rtvs/media/code-snippet-expansion.gif)

Dans ce cas, quand vous tapez `readc`, IntelliSense affiche une liste de saisie semi-automatique. En sélectionnant cette saisie semi-automatique dans la liste déroulante et en appuyant sur Tab, vous sélectionnez `readc`, et en rappuyant sur Tab vous développez l’extrait de code. (Pour cette raison, le développement de l’extrait de code est souvent évoqué comme « tapez l’extrait de code et appuyez deux fois sur Tab »). Dans la plupart des cas, le premier appui sur Tab effectue la sélection IntelliSense et le deuxième appui déclenche le développement.

Pour voir tous les extraits de code disponibles, ouvrez la boîte de dialogue **Outils > Gestionnaire des extraits de Code...** (Ctrl+K,B) et sélectionnez **R** pour **Langage**. Développez les groupes, puis sélectionnez les extraits de code individuels pour afficher une description et le texte de raccourci :

![Boîte de dialogue Extraits de code pour R](~/rtvs/media/code-snippet-dialog.png)

Pour créer des extraits de code personnalisés, suivez les instructions de [Procédure pas à pas : création d’un extrait de code](../ide/walkthrough-creating-a-code-snippet.md). En fin de compte, un extrait de code est un simple fichier XML. Par exemple, ce qui suit est l’extrait de code pour l’opération de barre verticale (raccourci `>`)

Notez qu’un extrait de code est un simple fichier XML. Voici l’extrait de code pour l’opérateur de barre verticale :

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

