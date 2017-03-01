---
title: Filtres de Service des commandes importantes pour langage | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- language services, filters
- language services, commands to support
ms.assetid: 4948c494-3d4d-4f50-b3f9-959e73f90e4d
caps.latest.revision: 16
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
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
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: f6b5bad11c47074c29f3b319678419f1e42ab91b
ms.lasthandoff: 02/22/2017

---
# <a name="important-commands-for-language-service-filters"></a>Commandes importantes pour les filtres de Service de langage
Si vous souhaitez créer un filtre de service de langage complet, envisagez de gérer les commandes suivantes. La liste complète des identificateurs de commande est définie dans le <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>énumération pour le code managé et l’en-tête de Stdidcmd.h de fichiers pour non managée [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] code.</xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> Vous pouvez trouver le fichier Stdidcmd.h *chemin d’installation de Visual Studio SDK*\VisualStudioIntegration\Common\Inc.  
  
## <a name="commands-to-handle"></a>Commandes pour la poignée  
  
> [!NOTE]
>  Il n’est pas obligatoire pour filtrer toutes les commandes dans le tableau suivant.  
  
|Commande|Description|  
|-------------|-----------------|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID></xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Envoyé lorsque l’utilisateur clique. Cette commande indique qu’il est temps de proposer un menu contextuel. Si vous ne gérez pas cette commande, l’éditeur de texte fournit un menu de raccourci par défaut sans les commandes spécifiques au langage. Pour inclure vos propres commandes de ce menu, gérer la commande et afficher un menu contextuel vous-même.|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID></xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|En général, envoyées lorsque l’utilisateur tape CTRL + J. Appelez le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A>méthode sur le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>pour afficher la zone de saisie semi-automatique d’instruction.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> </xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A>|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID></xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Envoyé lorsque l’utilisateur tape un caractère. Surveillez cette commande pour déterminer le moment de la saisie d’un caractère déclencheur et pour fournir la déclaration de fin, des conseils de méthode et des marqueurs de texte, telles que la coloration de syntaxe, la correspondance des accolades et des marqueurs d’erreur. Appelez le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A>méthode sur le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>pour compléter l’instruction et la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow.SetMethodData%2A>méthode sur le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow>pour obtenir des conseils (méthode).</xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow> </xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow.SetMethodData%2A> </xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> </xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> Pour prendre en charge des marqueurs de texte, surveiller cette commande pour déterminer si le caractère tapé requiert que vous mettez à jour vos marques.|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID></xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Envoyé lorsque l’utilisateur tape la touche ENTRÉE. Surveiller cette commande pour déterminer le moment fermer une fenêtre d’info-bulle de méthode en appelant la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A>méthode sur le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData>.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData> </xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A> Par défaut, la vue gère cette commande.|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID></xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Envoyé lorsque l’utilisateur tape la touche Retour arrière. Moniteur permettant de déterminer le moment de faire disparaître une fenêtre d’info-bulle de méthode en appelant la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A>méthode sur le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData>.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData> </xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A> Par défaut, la vue gère cette commande.|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID></xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Envoyé à partir d’un menu ou une touche de raccourci. Appelez le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateTipWindow%2A>méthode sur le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>pour mettre à jour la fenêtre d’info-bulle avec les informations de paramètre.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> </xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateTipWindow%2A>|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID></xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Envoyé lorsque l’utilisateur pointe sur une variable ou place le curseur sur une variable et sélectionne **Infos** de **IntelliSense** dans les **modifier** menu. Retourner le type de la variable dans une info-bulle en appelant la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateTipWindow%2A>méthode sur le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> </xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateTipWindow%2A> Si le débogage est actif, le Conseil doit également indiquer la valeur de la variable.|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID></xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|En général, envoyées lorsque l’utilisateur tape CTRL + espace. Cette commande indique le service de langage pour appeler la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A>méthode sur le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> </xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A>|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID></xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID><br /><br /> <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID></xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Envoyé à partir d’un menu, généralement **commenter la sélection** ou **ne pas commenter la sélection** de **avancé** dans les **modifier** menu. <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>Indique que l’utilisateur souhaite commenter le texte sélectionné ; <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>indique que l’utilisateur souhaite ne pas commenter le texte sélectionné.</xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID></xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> Ces commandes peuvent être implémentés que par le service de langage.|  
  
## <a name="see-also"></a>Voir aussi  
 [Développement d’un Service de langage hérité](../../extensibility/internals/developing-a-legacy-language-service.md)
