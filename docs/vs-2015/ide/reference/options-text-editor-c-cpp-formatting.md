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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 767bb04bcfe14c8cafbe69e5cb19ecbd8082ee40
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54770637"
---
# <a name="options-text-editor-cc-formatting"></a>Options, Éditeur de texte, C/C++, Mise en forme
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
Vous permet de modifier le comportement par défaut de l'Éditeur de code lorsque vous programmez en C ou C++.  
  
 Pour accéder à cette page, dans la boîte de dialogue **Options**, dans le volet gauche, développez **Éditeur de texte**, développez **C/C++**, puis cliquez sur **Mise en forme**.  
  
> [!NOTE]
>  Il est possible que pour certains des éléments de l’interface utilisateur de Visual Studio, votre ordinateur affiche des noms ou des emplacements différents de ceux indiqués dans les instructions suivantes. L'édition de Visual Studio dont vous disposez et les paramètres que vous utilisez déterminent ces éléments. Pour plus d’informations, consultez [Personnalisation des paramètres de développement dans Visual Studio](http://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## <a name="cc-options"></a>Options C/C++  
 **Activer les info-bulles Info express automatique**  
 Cette case à cocher permet d’activer ou de désactiver la fonctionnalité IntelliSense Info express.  
  
## <a name="inactive-code"></a>Code inactif  
 **Afficher les blocs de code inactifs**  
 Le code qui est inactif en raison de déclarations `#ifdef` est colorisé différemment pour vous aider à l'identifier.  
  
 **Désactiver l’opacité du code inactif**  
 Le code inactif peut être identifié en utilisant de la couleur au lieu de la transparence.  
  
 **Pourcentage d’opacité du code inactif**  
 Le degré d'opacité des blocs de code inactifs peut être personnalisé.  
  
## <a name="indentation"></a>Indentation  
 **Mettre en retrait les accolades**  
 Vous pouvez configurer la manière dont les accolades sont alignées lorsque vous appuyez sur ENTRÉE après avoir commencé un bloc de code, tel qu'une fonction ou une boucle `for`. Les accolades peuvent être alignées avec le premier caractère du bloc de code ou mises en retrait.  
  
 **Retrait automatique sur les onglets**  
 Vous pouvez configurer ce qui arrive sur la ligne de code actuelle lorsque vous appuyez sur la touche de tabulation. La ligne est mise en retrait ou un onglet est inséré.  
  
## <a name="miscellaneous"></a>Divers  
 **Énumérer les commentaires dans la fenêtre Liste des tâches**  
 L'éditeur peut rechercher des mots prédéfinis dans les commentaires de fichiers sources ouverts. Il crée une entrée dans la fenêtre **Liste des tâches** pour tous les mots clés qu’il trouve.  
  
 **Surligner les jetons correspondants**  
 Lorsque le curseur se trouve à côté d'une accolade, l'éditeur peut mettre en surbrillance l'accolade correspondante afin que vous puissiez consulter le code contenu plus facilement.  
  
## <a name="outlining"></a>mode Plan  
 **Passer en mode Plan à l’ouverture des fichiers**  
 Lorsque vous ouvrez un fichier dans l’éditeur de texte, vous pouvez activer la fonctionnalité mode Plan. Pour plus d’informations, voir [Mode Plan](../../ide/outlining.md). Lorsque cette option est sélectionnée, la fonctionnalité mode Plan est activée à l’ouverture d’un fichier.  
  
 **Mode Plan automatique des blocs #pragma region**  
 Quand cette option est sélectionnée, le mode Plan automatique pour les [directives de pragma](http://msdn.microsoft.com/library/9867b438-ac64-4e10-973f-c3955209873f) est activé. Cela vous permet de développer ou de réduire les blocs de région pragma en mode Plan.  
  
 **Mode Plan automatique des blocs d’instruction**  
 Lorsque cette option est sélectionnée, le mode Plan automatique est activé pour les constructions d'instruction suivantes :  
  
-   [if-else](http://msdn.microsoft.com/library/d9a1d562-8cf5-4bd4-9ba7-8ad970cd25b2)  
  
-   [switch, instruction (C++)](http://msdn.microsoft.com/library/6c3f3ed3-5593-463c-8f4b-b33742b455c6)  
  
-   [while, instruction (C++)](http://msdn.microsoft.com/library/358dbe76-5e5e-4af5-b575-c2293c636899)  
  
## <a name="see-also"></a>Voir aussi  
 [Général, Environnement, boîte de dialogue Options](../../ide/reference/general-environment-options-dialog-box.md)   
 [Utilisation de la fonctionnalité IntelliSense](../../ide/using-intellisense.md)
