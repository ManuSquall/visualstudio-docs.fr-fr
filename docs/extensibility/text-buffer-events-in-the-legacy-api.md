---
title: "Événements de mémoire tampon de texte dans l’API héritée | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - text buffer events
ms.assetid: 9be49e9f-1864-41c2-8a3c-f66895881341
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
ms.openlocfilehash: 39ac6a711278950d09ed16b157fc89980144e3d0
ms.lasthandoff: 02/22/2017

---
# <a name="text-buffer-events-in-the-legacy-api"></a>Événements de mémoire tampon de texte dans l’API héritée
L’objet de mémoire tampon de texte émet plusieurs événements différents qui vous permettent de répondre à différentes situations.  
  
 Lorsque vous utilisez l’API héritée, vous devez implémenter les interfaces suivantes afin de recevoir des notifications de modification de la mémoire tampon de texte. Exposer les interfaces dans la mémoire tampon de texte à l’aide de la `IConnectionPointContainer` interface sur la mémoire tampon de texte pour recevoir une notification de la ligne modifiée à partir de la mémoire tampon. Pour plus d’informations, consultez [Comment : s’inscrire aux événements de mémoire tampon de texte avec l’API héritée](../extensibility/how-to-register-for-text-buffer-events-with-the-legacy-api.md). Dans le cas de `IVsTextStreamEvents` ou `IVsTextLinesEvents` les interfaces, les modifications sont retournées dans l’une ou deux dimensions coordonnées, respectivement.  
  
## <a name="text-buffer-interfaces"></a>Interfaces de mémoire tampon de texte  
 Voici les interfaces implémentées par l’objet de mémoire tampon de texte.  
  
|Interface|Description|  
|---------------|-----------------|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompoundAction></xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompoundAction>|Permet la création d’actions composées (autrement dit, les actions qui sont regroupées en une unité d’annulation/de rétablissement unique).|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData></xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData>|Active la persistance des données du document gérées par la mémoire tampon de texte.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer></xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>|Fournit des services de base ; utilisé par de nombreux clients.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines></xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>|Fournit des lecture et en écriture à l’aide de coordonnées à deux dimensions. Hérite de `IVsTextBuffer`.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextScanner></xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextScanner>|Offre un accès séquentiel, en fonction du flux de texte dans la mémoire tampon rapide.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream></xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream>|Fournit des lire et écrire des fonctionnalités à l’aide des coordonnées unidimensionnelles. Hérite de `IVsTextBuffer`.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserData></xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserData>|Fournit l’accès à une collection générique de propriétés. La propriété la plus importante est le nom ou le nom, de la mémoire tampon. Vous pouvez stocker vos propres données aléatoires dans la mémoire tampon avec cette interface par la création d’un GUID et son utilisation en tant que clé.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer></xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>|Prend en charge les points de connexion pour les événements.|  
  
## <a name="text-buffer-event-interfaces"></a>Interfaces d’événements de mémoire tampon de texte  
 Voici les interfaces de notification d’événement de mémoire tampon de texte.  
  
|Interface|Description|  
|---------------|-----------------|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferEvents></xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferEvents>|Notifie les clients lorsqu’un nouveau service de langage est associé à une mémoire tampon de texte.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferDataEvents></xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferDataEvents>|Notifie les clients lors de l’initialisation de la mémoire tampon de texte et lorsque des modifications sont apportées aux données dans la mémoire tampon de texte.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStreamEvents></xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStreamEvents>|Notifie les clients des modifications apportées à la mémoire tampon sous-jacente dans les coordonnées de la dimension.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLinesEvents></xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLinesEvents>|Notifie les clients des modifications apportées à la mémoire tampon sous-jacente dans les coordonnées à deux dimensions.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserDataEvents></xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserDataEvents>|Notifie les clients des modifications apportées aux données utilisateur.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsPreliminaryTextChangeCommitEvents></xref:Microsoft.VisualStudio.TextManager.Interop.IVsPreliminaryTextChangeCommitEvents>|Notifie les clients du dernier mouvement de validation pour déclencher l’événement et fournit la plage de texte modifié. Le `IVsPreliminaryTextChangeCommitEvents` interface n’est pas déclenchée en réponse à annuler ou rétablir les commandes. Événements se déclenchent uniquement pour les mémoires tampons qui ont un gestionnaire d’annulation. `IVsPreliminaryTextChangeCommitEvents`se déclenche avant les autres événements, tels que de tabulation, afin de vous assurer que les autres événements ne modifient pas le texte avant que les modifications soient validées. Le VSPackage doit surveiller un le `IVsPreliminaryTextChangeCommitEvents` interface ou `IVsFinalTextChangeCommitEvents` interface, mais pas les deux.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsFinalTextChangeCommitEvents></xref:Microsoft.VisualStudio.TextManager.Interop.IVsFinalTextChangeCommitEvents>|Notifie les clients du dernier mouvement de validation pour déclencher l’événement et fournit la plage de texte modifié. Le `IVsFinalTextChangeCommitEvents` interface n’est pas déclenchée en réponse à annuler ou rétablir les commandes. Événements se déclenchent uniquement pour les mémoires tampons qui ont un gestionnaire d’annulation. `IVsFinalTextChangeCommitEvents`est conçue pour une utilisation uniquement par les services de langage ou d’autres objets qui ont un contrôle complet sur la modification. Le VSPackage doit surveiller un le `IVsPreliminaryTextChangeCommitEvents` interface ou `IVsFinalTextChangeCommitEvents` interface, mais pas les deux.|  
  
## <a name="see-also"></a>Voir aussi  
 [L’accès à la mémoire tampon de texte à l’aide de l’API héritée](../extensibility/accessing-the-text-buffer-by-using-the-legacy-api.md)   
 [Comment : s’inscrire aux événements de mémoire tampon de texte avec l’API héritée](../extensibility/how-to-register-for-text-buffer-events-with-the-legacy-api.md)
