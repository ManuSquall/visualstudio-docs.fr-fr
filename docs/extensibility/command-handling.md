---
title: Gestion des commandes | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - command handling
ms.assetid: 78f67d92-77f7-45cb-ad75-6e3346379cc3
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 542277c5d8ab1b9b130f31bbb06215d8da7bc2ef
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31099956"
---
# <a name="command-handling"></a>Gestion des commandes
Votre éditeur peut définir de nouvelles commandes. Commandes sont généralement affichées dans un menu, une barre d’outils, ou dans un menu contextuel.  
  
 Pour plus d’informations sur la définition des menus et commandes, consultez [commandes, Menus et barres d’outils](../extensibility/internals/commands-menus-and-toolbars.md).  
  
 Un service de langage peut contrôler les menus contextuels sont affichés dans l’éditeur, en interceptant le <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> énumération. Ou bien, vous pouvez contrôler le menu contextuel sur une base par marqueur. Pour plus d’informations, consultez [commandes Important pour les filtres de Service de langage](../extensibility/internals/important-commands-for-language-service-filters.md).  
  
## <a name="adding-commands-to-the-editor-context-menu"></a>Ajout de commandes au Menu contextuel Éditeur  
 Pour ajouter une commande au menu contextuel, vous devez d’abord définir un ensemble de commandes de menu qui appartiennent à un groupe spécifique. L’exemple suivant est extrait à partir du fichier .vsct généré dans le cadre de la procédure pas à pas [procédure pas à pas : ajout de fonctionnalités à un éditeur personnalisé](../extensibility/walkthrough-adding-features-to-a-custom-editor.md):  
  
 \<Guid du menu = « guidCustomEditorCmdSet » id = « IDMX_RTF » priorité = « 0 x 0000 » type = « Contexte » >  
  
 \<Guid du parent = « guidCustomEditorCmdSet » id = « 0 » / >  
  
 \<Chaînes >  
  
 \<ButtonText > Menu contextuel de CustomEditor\</ButtonText >  
  
 \<CommandName > CustomEditorContextMenu\</CommandName >  
  
 \</ Chaînes de >  
  
 \</ Menu >  
  
 \</ Menus >  
  
 Le texte ci-dessus ajoute une commande de menu contextuel avec le texte **Menu contextuel de CustomEditor**. Le GUID de Menu est que de l’ensemble de commandes qui est créé avec cet éditeur, et le type est « Contexte ».  
  
 Vous pouvez également utiliser des commandes prédéfinies qui ne doivent pas être définies dans le fichier .vsct. Par exemple, si vous examinez le fichier EditorPane.cs généré par le modèle de Package Visual Studio, vous recherchez qui un jeu de commandes prédéfinies, telles que <xref:Microsoft.VisualStudio.VSConstants.VSStd97CmdID> défini par <xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97>, sont gérées dans les gestionnaires de commandes telles que la méthode onSelectAll.  
  
## <a name="see-also"></a>Voir aussi  
 [Commandes, menus et barres d’outils](../extensibility/internals/commands-menus-and-toolbars.md)