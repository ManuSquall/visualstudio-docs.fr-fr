---
title: Événements de mémoire tampon de texte dans l’API hérité | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - text buffer events
ms.assetid: 9be49e9f-1864-41c2-8a3c-f66895881341
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ab2812d30c0f02063e9ed3672e9b01855c77da22
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="text-buffer-events-in-the-legacy-api"></a>Événements de mémoire tampon de texte dans l’API hérité
L’objet de mémoire tampon de texte émet plusieurs événements différents qui vous permettent de répondre à différentes situations.  
  
 Lorsque vous utilisez l’API héritée, vous devez implémenter les interfaces suivantes afin de recevoir des notifications de modification de la mémoire tampon de texte. Exposer les interfaces dans la mémoire tampon de texte à l’aide de la `IConnectionPointContainer` interface sur la mémoire tampon de texte pour recevoir une notification de la ligne modifiée à partir de la mémoire tampon. Pour plus d’informations, consultez [Comment : s’inscrire aux événements de mémoire tampon de texte avec l’API héritée](../extensibility/how-to-register-for-text-buffer-events-with-the-legacy-api.md). Dans le cas de `IVsTextStreamEvents` ou `IVsTextLinesEvents` interfaces, les modifications sont retournées dans l’une ou deux dimensions coordonnées, respectivement.  
  
## <a name="text-buffer-interfaces"></a>Interfaces de mémoire tampon de texte  
 Voici les interfaces implémentées par l’objet de mémoire tampon de texte.  
  
|Interface|Description|  
|---------------|-----------------|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompoundAction>|Permet la création d’actions composées (autrement dit, les actions qui sont regroupées dans une unité d’annulation/de rétablissement unique).|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData>|Active la persistance des données du document gérées par la mémoire tampon de texte.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>|Fournit des services de base ; utilisé par de nombreux clients.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>|Fournit de lecture et en écriture à l’aide de coordonnées à deux dimensions. Hérite de `IVsTextBuffer`.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextScanner>|Offre un accès séquentiel, orienté flux de données à du texte dans la mémoire tampon rapide.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream>|Fournit des lire et écrire des fonctions à l’aide de coordonnées unidimensionnelles. Hérite de `IVsTextBuffer`.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserData>|Fournit l’accès à une collection générique de propriétés. La propriété la plus importante est le nom ou le moniker, de la mémoire tampon. Vous pouvez stocker vos propres données aléatoires dans la mémoire tampon avec cette interface par la création d’un GUID et l’utiliser en tant que clé.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>|Prend en charge les points de connexion pour les événements.|  
  
## <a name="text-buffer-event-interfaces"></a>Interfaces d’événements de mémoire tampon de texte  
 Voici les interfaces de notification d’événement de mémoire tampon de texte.  
  
|Interface|Description|  
|---------------|-----------------|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferEvents>|Notifie les clients lorsqu’un nouveau service de langage est associé à une mémoire tampon de texte.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferDataEvents>|Notifie les clients lors de l’initialisation de mémoire tampon de texte et lorsque des modifications sont apportées aux données dans la mémoire tampon de texte.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStreamEvents>|Notifie les clients des modifications apportées à la mémoire tampon sous-jacente dans les coordonnées de la dimension.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLinesEvents>|Notifie les clients des modifications apportées à la mémoire tampon sous-jacente en utilisant les coordonnées à deux dimensions.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserDataEvents>|Notifie les clients des modifications apportées aux données utilisateur.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsPreliminaryTextChangeCommitEvents>|Notifie les clients du dernier mouvement de la validation de déclencher l’événement et fournit la plage de texte modifié. Le `IVsPreliminaryTextChangeCommitEvents` interface n’est pas déclenché en réponse à annuler ou rétablir les commandes. Événements se déclenchent uniquement pour les mémoires tampons qui ont un gestionnaire d’annulation. `IVsPreliminaryTextChangeCommitEvents` se déclenche avant les autres événements, tels que de tabulation, afin de vous assurer que les autres événements ne modifient pas le texte avant que les modifications soient validées. Votre VSPackage doit surveiller un le `IVsPreliminaryTextChangeCommitEvents` interface ou le `IVsFinalTextChangeCommitEvents` interface, mais pas les deux.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsFinalTextChangeCommitEvents>|Notifie les clients du dernier mouvement de la validation de déclencher l’événement et fournit la plage de texte modifié. Le `IVsFinalTextChangeCommitEvents` interface n’est pas déclenché en réponse à annuler ou rétablir les commandes. Événements se déclenchent uniquement pour les mémoires tampons qui ont un gestionnaire d’annulation. `IVsFinalTextChangeCommitEvents` est destinée uniquement aux services de langage ou d’autres objets qui ont un contrôle complet sur la modification. Votre VSPackage doit surveiller un le `IVsPreliminaryTextChangeCommitEvents` interface ou le `IVsFinalTextChangeCommitEvents` interface, mais pas les deux.|  
  
## <a name="see-also"></a>Voir aussi  
 [L’accès à la mémoire tampon de texte à l’aide de l’API héritée](../extensibility/accessing-the-text-buffer-by-using-the-legacy-api.md)   
 [Comment : s’inscrire aux événements de mémoire tampon de texte avec l’API hérité](../extensibility/how-to-register-for-text-buffer-events-with-the-legacy-api.md)