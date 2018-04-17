---
title: Filtres de Service des commandes importantes pour la langue | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- language services, filters
- language services, commands to support
ms.assetid: 4948c494-3d4d-4f50-b3f9-959e73f90e4d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 1e7affdbcad2b935a05420a2817c5d8bda5cd9cf
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="important-commands-for-language-service-filters"></a>Commandes importants pour les filtres de Service de langage
Si vous souhaitez créer un filtre de service de langage complet, envisagez de gérer les commandes suivantes. La liste complète des identificateurs de commande est définie dans le <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> énumération pour le code managé et l’en-tête de Stdidcmd.h de fichiers pour non managée [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] code. Vous pouvez trouver le fichier Stdidcmd.h *chemin d’installation de Visual Studio SDK*\VisualStudioIntegration\Common\Inc.  
  
## <a name="commands-to-handle"></a>Commandes à traiter  
  
> [!NOTE]
>  Il n’est pas obligatoire pour filtrer toutes les commandes dans le tableau suivant.  
  
|Commande|Description|  
|-------------|-----------------|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Envoyé lorsque l’utilisateur clique. Cette commande indique qu’il est temps de fournir un menu contextuel. Si vous ne gérez pas cette commande, l’éditeur de texte fournit un menu de raccourci par défaut sans les commandes spécifiques au langage. Pour inclure vos propres commandes de ce menu, gérer la commande et afficher un menu contextuel vous-même.|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|En général envoyé lorsque l’utilisateur tape CTRL + J. Appelez le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> méthode sur le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> d’afficher la zone de saisie semi-automatique d’instruction.|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Envoyé lorsque l’utilisateur tape un caractère. Analyse de cette commande pour déterminer quand la saisie d’un caractère déclencheur et pour fournir l’instruction saisie semi-automatique, des conseils de méthode et des marqueurs de texte, telles que la coloration de syntaxe, la correspondance des accolades et des marqueurs d’erreur. Appelez le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> méthode sur le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> pour la saisie semi-automatique des instructions et la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow.SetMethodData%2A> méthode sur le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow> pour obtenir des conseils de la méthode. Pour prendre en charge des marqueurs de texte, surveiller cette commande pour déterminer si le caractère tapé requiert que vous mettez à jour vos marqueurs.|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Envoyé lorsque l’utilisateur tape la touche ENTRÉE. Surveiller cette commande pour déterminer le moment de faire disparaître une fenêtre d’info-bulle de méthode en appelant le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A> méthode sur le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData>. Par défaut, l’affichage de texte gère cette commande.|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Envoyé lorsque l’utilisateur tape la touche Retour arrière. Analyse pour déterminer le moment de faire disparaître une fenêtre d’info-bulle de méthode en appelant le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A> méthode sur le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData>. Par défaut, l’affichage de texte gère cette commande.|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Envoyé à partir d’un menu ou une touche de raccourci. Appelez le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateTipWindow%2A> méthode sur le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> pour mettre à jour de la fenêtre d’info-bulle avec les informations de paramètre.|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Envoyé lorsque l’utilisateur pointe sur une variable ou place le curseur sur une variable et sélectionne **Info Express** de **IntelliSense** dans les **modifier** menu. Le type de la variable de retour dans une info-bulle en appelant le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateTipWindow%2A> méthode sur le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>. Si le débogage est actif, l’info-bulle doit également indiquer la valeur de la variable.|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|En général envoyé lorsque l’utilisateur tape CTRL + espace. Cette commande indique le service de langage pour appeler le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> méthode sur le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>.|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID><br /><br /> <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Envoyé à partir d’un menu, généralement **commenter la sélection** ou **ne pas commenter la sélection** de **avancé** dans les **modifier** menu. <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> Indique que l’utilisateur souhaite commenter le texte sélectionné ; <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> indique que l’utilisateur souhaite ne pas commenter le texte sélectionné. Ces commandes peuvent être implémentées uniquement par le service de langage.|  
  
## <a name="see-also"></a>Voir aussi  
 [Développement d’un service de langage hérité](../../extensibility/internals/developing-a-legacy-language-service.md)