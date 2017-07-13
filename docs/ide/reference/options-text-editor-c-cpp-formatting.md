---
title: "Options, Éditeur de texte, C/C++, Mise en forme | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.C/C++.Formatting.General
- VS.ToolsOptionsPages.Text_Editor.C%2fC%2b%2b.Formatting.General
dev_langs:
- C++
helpviewer_keywords:
- Text Editor Options dialog box, formatting
ms.assetid: cb6f1cbb-5305-48da-a8e8-33fd70775d46
caps.latest.revision: 16
author: kempb
ms.author: kempb
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
ms.sourcegitcommit: 5ea9179ad37514ffad4876177b05150eecc22def
ms.openlocfilehash: 41cca3051eaf1bfdc90f6616900699b8996033b0
ms.contentlocale: fr-fr
ms.lasthandoff: 05/24/2017

---
# Options, Éditeur de texte, C/C++, Mise en forme
<a id="options-text-editor-cc-formatting" class="xliff"></a>
Vous permet de modifier le comportement par défaut de l'Éditeur de code lorsque vous programmez en C ou C++.  
  
 Pour accéder à cette page, dans la boîte de dialogue **Options**, dans le volet gauche, développez **Éditeur de texte**, développez **C/C++**, puis cliquez sur **Mise en forme**.  
  
> [!NOTE]
>  Il est possible que pour certains des éléments de l’interface utilisateur de Visual Studio, votre ordinateur affiche des noms ou des emplacements différents de ceux indiqués dans les instructions suivantes. L'édition de Visual Studio dont vous disposez et les paramètres que vous utilisez déterminent ces éléments. Pour plus d’informations, consultez [Personnaliser l’IDE Visual Studio](../../ide/personalizing-the-visual-studio-ide.md).  
  
## Options C/C++
<a id="cc-options" class="xliff"></a>  
 **Activer les info-bulles Info express automatique**  
 Cette case à cocher permet d’activer ou de désactiver la fonctionnalité IntelliSense Info express.  
  
## Code inactif
<a id="inactive-code" class="xliff"></a>  
 **Afficher les blocs de code inactifs**  
 Le code qui est inactif en raison de déclarations `#ifdef` est colorisé différemment pour vous aider à l'identifier.  
  
 **Désactiver l’opacité du code inactif**  
 Le code inactif peut être identifié en utilisant de la couleur au lieu de la transparence.  
  
 **Pourcentage d’opacité du code inactif**  
 Le degré d'opacité des blocs de code inactifs peut être personnalisé.  
  
## Indentation
<a id="indentation" class="xliff"></a>  
 **Mettre en retrait les accolades**  
 Vous pouvez configurer la manière dont les accolades sont alignées lorsque vous appuyez sur ENTRÉE après avoir commencé un bloc de code, tel qu'une fonction ou une boucle `for`. Les accolades peuvent être alignées avec le premier caractère du bloc de code ou mises en retrait.  
  
 **Retrait automatique sur les onglets**  
 Vous pouvez configurer ce qui arrive sur la ligne de code actuelle lorsque vous appuyez sur la touche de tabulation. La ligne est mise en retrait ou un onglet est inséré.  
  
## Divers
<a id="miscellaneous" class="xliff"></a>  
 **Énumérer les commentaires dans la fenêtre Liste des tâches**  
 L'éditeur peut rechercher des mots prédéfinis dans les commentaires de fichiers sources ouverts. Il crée une entrée dans la fenêtre **Liste des tâches** pour tous les mots clés qu’il trouve.  
  
 **Surligner les jetons correspondants**  
 Lorsque le curseur se trouve à côté d'une accolade, l'éditeur peut mettre en surbrillance l'accolade correspondante afin que vous puissiez consulter le code contenu plus facilement.  
  
## Mode Plan
<a id="outlining" class="xliff"></a>  
 **Passer en mode Plan à l’ouverture des fichiers**  
 Lorsque vous ouvrez un fichier dans l’éditeur de texte, vous pouvez activer la fonctionnalité mode Plan. Pour plus d’informations, voir [Mode Plan](../../ide/outlining.md). Lorsque cette option est sélectionnée, la fonctionnalité mode Plan est activée à l’ouverture d’un fichier.  
  
 **Mode Plan automatique des blocs #pragma region**  
 Quand cette option est sélectionnée, le mode Plan automatique pour les [directives de pragma](/cpp/preprocessor/pragma-directives-and-the-pragma-keyword) est activé. Cela vous permet de développer ou de réduire les blocs de région pragma en mode Plan.  
  
 **Mode Plan automatique des blocs d’instruction**  
 Lorsque cette option est sélectionnée, le mode Plan automatique est activé pour les constructions d'instruction suivantes :  
  
-   [if-else](/dotnet/csharp/language-reference/keywords/if-else)  
  
-   [switch, instruction (C++)](/cpp/cpp/switch-statement-cpp)  
  
-   [while, instruction (C++)](/cpp/cpp/while-statement-cpp)  
  
## Voir aussi
<a id="see-also" class="xliff"></a>  
 [Général, Environnement, boîte de dialogue Options](../../ide/reference/general-environment-options-dialog-box.md)   
 [Utilisation de la fonctionnalité IntelliSense](../../ide/using-intellisense.md)
