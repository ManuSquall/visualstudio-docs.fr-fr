---
title: Gestion des commandes | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - command handling
ms.assetid: 78f67d92-77f7-45cb-ad75-6e3346379cc3
caps.latest.revision: 21
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 563f38cd2dc3854918fe637fdc11afe1d1a49b64
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68184371"
---
# <a name="command-handling"></a>Gestion des commandes
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Votre éditeur peut définir de nouvelles commandes. Les commandes sont généralement affichées dans un menu, dans une barre d’outils ou dans un menu contextuel.  
  
 Pour plus d’informations sur la définition des commandes et des menus, consultez [commandes, menus et barres d’outils](../extensibility/internals/commands-menus-and-toolbars.md).  
  
 Un service de langage peut contrôler les menus contextuels qui sont affichés dans l’éditeur, en interceptant l' <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> énumération. Vous pouvez également contrôler le menu contextuel sur une base par marqueur. Pour plus d’informations, consultez [commandes importantes pour les filtres du service de langage](../extensibility/internals/important-commands-for-language-service-filters.md).  
  
## <a name="adding-commands-to-the-editor-context-menu"></a>Ajout de commandes au menu contextuel de l’éditeur  
 Pour ajouter une commande au menu contextuel, vous devez d’abord définir un ensemble de commandes de menu appartenant à un groupe spécifique. L’exemple suivant est extrait du fichier. vsct généré dans le cadre de la procédure pas à pas [: ajout de fonctionnalités à un éditeur personnalisé](../extensibility/walkthrough-adding-features-to-a-custom-editor.md):  
  
 \<Menu guid="guidCustomEditorCmdSet" id="IDMX_RTF" priority="0x0000" type="Context">  
  
 \<Parent guid="guidCustomEditorCmdSet" id="0"/>  
  
 \<Strings>  
  
 \<ButtonText>Menu contextuel CustomEditor\</ButtonText>  
  
 \<CommandName>CustomEditorContextMenu\</CommandName>  
  
 \</Strings>  
  
 \</Menu>  
  
 \</Menus>  
  
 Le texte ci-dessus ajoute une commande de menu contextuel avec le **menu contextuel texte CustomEditor**. Le GUID de menu est celui du jeu de commandes créé avec cet éditeur et le type est « context ».  
  
 Vous pouvez également utiliser des commandes prédéfinies qui n’ont pas besoin d’être définies dans le fichier. vsct. Par exemple, si vous examinez le fichier EditorPane.cs généré par le modèle de package Visual Studio, vous constatez qu’un ensemble de commandes prédéfinies, telles que <xref:Microsoft.VisualStudio.VSConstants.VSStd97CmdID> définies par <xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97> , sont gérées dans des gestionnaires de commandes tels que la méthode onSelectAll.  
  
## <a name="see-also"></a>Voir aussi  
 [Commandes, menus et barres d’outils](../extensibility/internals/commands-menus-and-toolbars.md)
