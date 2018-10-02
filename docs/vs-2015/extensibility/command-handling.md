---
title: Gestion des commandes | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - command handling
ms.assetid: 78f67d92-77f7-45cb-ad75-6e3346379cc3
caps.latest.revision: 21
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 32bfe8ec88d0e2ad5a2b765dcff01f543fe59c18
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47502594"
---
# <a name="command-handling"></a>Gestion des commandes
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [gestion des commandes](https://docs.microsoft.com/visualstudio/extensibility/command-handling).  
  
Votre éditeur peut définir de nouvelles commandes. Commandes sont généralement affichées dans un menu sur une barre d’outils ou dans un menu contextuel.  
  
 Pour plus d’informations sur la définition des menus et commandes, consultez [commandes, Menus et barres d’outils](../extensibility/internals/commands-menus-and-toolbars.md).  
  
 Un service de langage peut contrôler les menus contextuels sont affichés dans l’éditeur, en interceptant le <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> énumération. Alternativement, vous pouvez contrôler le menu contextuel sur une base par marqueur. Pour plus d’informations, consultez [commandes importantes pour les filtres du Service de langage](../extensibility/internals/important-commands-for-language-service-filters.md).  
  
## <a name="adding-commands-to-the-editor-context-menu"></a>Ajout de commandes au Menu contextuel Éditeur  
 Pour ajouter une commande au menu contextuel, vous devez d’abord définir un ensemble de commandes de menu qui appartiennent à un groupe spécifique. L’exemple suivant est extrait à partir du fichier .vsct généré dans le cadre de la procédure pas à pas [procédure pas à pas : ajout de fonctionnalités à un éditeur personnalisé](../extensibility/walkthrough-adding-features-to-a-custom-editor.md):  
  
 \<Guid du menu = « guidCustomEditorCmdSet » id = « IDMX_RTF » priorité = « 0 x 0000 » type = « Contexte » >  
  
 \<Guid du parent = « guidCustomEditorCmdSet » id = « 0 » / >  
  
 \<Chaînes >  
  
 \<ButtonText > Menu contextuel de CustomEditor\</ButtonText >  
  
 \<CommandName > CustomEditorContextMenu\</CommandName >  
  
 \</ Chaînes >  
  
 \</ Menu >  
  
 \</ Menus >  
  
 Le texte ci-dessus ajoute une commande de menu contextuel avec le texte **Menu contextuel de CustomEditor**. Le GUID de Menu est que du jeu de commandes qui est créé avec cet éditeur, et le type est « Contexte ».  
  
 Vous pouvez également utiliser des commandes prédéfinies qui ne doivent pas être définis dans le fichier .vsct. Par exemple, si vous examinez le fichier EditorPane.cs généré par le modèle de Package Visual Studio, vous trouvez qui un ensemble de commandes prédéfinies, telles que <xref:Microsoft.VisualStudio.VSConstants.VSStd97CmdID> défini par <xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97>, sont gérées dans les gestionnaires de commandes telles que la méthode onSelectAll.  
  
## <a name="see-also"></a>Voir aussi  
 [Commandes, menus et barres d’outils](../extensibility/internals/commands-menus-and-toolbars.md)

