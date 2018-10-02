---
title: Options, Éditeur de texte, Tous les langages, Onglets | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.ResJSON.Tabs
- VS.ToolsOptionsPages.Text_Editor.JavaScript.Tabs
- VS.ToolsOptionsPages.Text_Editor.All_Languages.Tabs
helpviewer_keywords:
- indents, Code Editor
- Code Editor, default behavior
- tabs, setting in Code Editor
- All Languages Text Editor Options dialog box
- editors, Code Editor
- Code Editor, indenting
- Code Editor, tabs
ms.assetid: 7e208e1d-5e3a-4bf7-a27b-4417e3e049c7
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 107b12d7ac34f44dbffd67a3d15f124d85b64ddc
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47504307"
---
# <a name="options-text-editor-all-languages-tabs"></a>Options, Éditeur de texte, Tous les langages, Onglets
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [Options, éditeur de texte, tous les langages, onglets](https://docs.microsoft.com/visualstudio/ide/reference/options-text-editor-all-languages-tabs).  
  
  
Cette boîte de dialogue vous permet de modifier le comportement par défaut de l’éditeur de code. Ces paramètres s’appliquent également à d’autres éditeurs basés sur l’éditeur de code, tels que le mode Source du concepteur HTML. Pour afficher ces options, sélectionnez **Options** dans le menu **Outils**. Dans le dossier **Éditeur de texte**, développez le sous-dossier **Tous les langages**, puis choisissez **Onglets**.  
  
> [!CAUTION]
>  Cette page définit les options par défaut pour tous les langages de développement. N’oubliez pas que la réinitialisation d’une option dans cette boîte de dialogue entraîne la réinitialisation des options des onglets dans tous les langages quels que soient les choix effectués. Pour modifier les options de l’éditeur de texte pour un seul langage, développez le sous-dossier de ce langage et sélectionnez ses pages d’options.  
  
 Si des paramètres différents sont sélectionnés dans les pages d’options Onglets pour des langages de programmation particuliers, le message « Les paramètres de mise en retrait pour les formats de texte individuels sont en conflit » s’affiche pour les options **Mise en retrait** qui diffèrent. De plus, le message « Les paramètres de tabulation pour les formats de texte individuels sont en conflit » s’affiche pour les options **Onglets** qui diffèrent. Par exemple, ce rappel s’affiche si l’option **Retrait intelligent** est sélectionnée pour Visual Basic, mais l’option **Retrait de bloc** est sélectionnée pour Visual C++.  
  
> [!NOTE]
>  Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée. Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils** . Pour plus d’informations, consultez [Personnalisation des paramètres de développement dans Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## <a name="indenting"></a>Mise en retrait  
 Aucun.  
 Lorsque cette option est sélectionnée, les nouvelles lignes ne sont pas mises en retrait. Le point d'insertion est placé dans la première colonne d'une nouvelle ligne.  
  
 Bloc  
 Lorsque cette option est sélectionnée, les nouvelles lignes sont automatiquement mises en retrait. Le point d'insertion est placé sur le même point de départ que la ligne précédente.  
  
 Intelligente  
 Lorsque cette option est sélectionnée, les nouvelles lignes sont positionnées en fonction du contexte de code, selon les paramètres de mise en forme d’un autre code et les conventions IntelliSense de votre langage de développement. Cette option n’est pas disponible pour tous les langages de développement.  
  
 Par exemple, les lignes comprises entre une accolade ouvrante ( { ) et une accolade fermante ( } ) peuvent automatiquement être mises en retrait d’un taquet de tabulation supplémentaire à partir de la position des accolades alignées.  
  
## <a name="tabs"></a>Tabulations  
 Taille des tabulations  
 Définit la distance en espaces entre les taquets de tabulation. La valeur par défaut est quatre espaces.  
  
 Taille du retrait  
 Définit la taille, en espaces, d'une mise en retrait automatique. La valeur par défaut est quatre espaces. Des tabulations et/ou des espaces seront insérés pour occuper la taille spécifiée.  
  
 Insérer des espaces  
 Lorsque cette option est sélectionnée, les opérations de mise en retrait n’insèrent que des caractères d’espacement et non des caractères de tabulation. Par exemple, si **Taille du retrait** a la valeur 5, cinq espaces sont insérés lorsque vous appuyez sur la touche Tab ou cliquez sur le bouton **Augmenter le retrait** de la barre d’outils **Mise en forme**.  
  
 Conserver les tabulations  
 Lorsque cette option est sélectionnée, les opérations de mise en retrait insèrent autant de caractères de tabulation que possible. Chaque caractère de tabulation remplit le nombre d’espaces spécifié dans **Taille des tabulations**. Si la valeur de **Taille du retrait** n’est pas un multiple pair de la valeur de **Taille des tabulations**, des espaces sont ajoutés pour combler la différence.  
  
## <a name="see-also"></a>Voir aussi  
 [Options, Éditeur de texte, Tous les langages](../../ide/reference/options-text-editor-all-languages.md)   
 [Général, Environnement, boîte de dialogue Options](../../ide/reference/general-environment-options-dialog-box.md)



