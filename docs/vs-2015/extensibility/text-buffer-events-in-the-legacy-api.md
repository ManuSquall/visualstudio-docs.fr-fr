---
title: Événements de mémoire tampon de texte dans l’API héritée | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - text buffer events
ms.assetid: 9be49e9f-1864-41c2-8a3c-f66895881341
caps.latest.revision: 17
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e82fa31ca435d0c850a4d9e75e927cff9613b046
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68186402"
---
# <a name="text-buffer-events-in-the-legacy-api"></a>Événements de la mémoire tampon du texte dans l’API héritée
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

L’objet de mémoire tampon de texte émet plusieurs événements qui vous permettent de répondre à différentes situations.  
  
 Lorsque vous utilisez l’API héritée, vous devez implémenter les interfaces suivantes pour recevoir la notification des modifications apportées à la mémoire tampon de texte. Exposez les interfaces à la mémoire tampon de texte à l’aide de l' `IConnectionPointContainer` interface sur la mémoire tampon de texte pour recevoir la notification des modifications de ligne de la mémoire tampon. Pour plus d’informations, consultez [Comment : s’inscrire pour les événements de mémoire tampon de texte avec l’API héritée](../extensibility/how-to-register-for-text-buffer-events-with-the-legacy-api.md). Dans le cas d' `IVsTextStreamEvents` `IVsTextLinesEvents` interfaces ou, les modifications sont retournées dans les coordonnées à une ou deux dimensions, respectivement.  
  
## <a name="text-buffer-interfaces"></a>Interfaces de mémoire tampon de texte  
 Voici les interfaces implémentées par l’objet de mémoire tampon de texte.  
  
|Interface|Description|  
|---------------|-----------------|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompoundAction>|Active la création d’actions composées (autrement dit, les actions regroupées en une seule unité d’annulation/de rétablissement).|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData>|Active la persistance des données de document gérées par la mémoire tampon de texte.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>|Fournit des services de base. utilisé par de nombreux clients.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>|Fournit des fonctionnalités de lecture et d’écriture à l’aide de coordonnées à deux dimensions. Hérite de `IVsTextBuffer`.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextScanner>|Fournit un accès séquentiel rapide et orienté flux à du texte dans la mémoire tampon.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream>|Fournit des fonctionnalités de lecture et d’écriture à l’aide de coordonnées unidimensionnelles. Hérite de `IVsTextBuffer`.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserData>|Fournit l’accès à une collection générique de propriétés. La propriété la plus importante est le nom ou le moniker de la mémoire tampon. Vous pouvez stocker vos propres données aléatoires dans la mémoire tampon avec cette interface en créant un GUID et en l’utilisant comme clé.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>|Prend en charge les points de connexion pour les événements.|  
  
## <a name="text-buffer-event-interfaces"></a>Interfaces d’événements de mémoire tampon de texte  
 Voici les interfaces pour la notification d’événements de mémoire tampon de texte.  
  
|Interface|Description|  
|---------------|-----------------|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferEvents>|Avertit les clients lorsqu'un nouveau service de langage est associé à une mémoire tampon de texte.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferDataEvents>|Avertit les clients lorsqu’une mémoire tampon de texte est initialisée et lorsque des modifications sont apportées aux données dans la mémoire tampon de texte.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStreamEvents>|Avertit les clients des modifications apportées à la mémoire tampon de texte sous-jacente en coordonnées unidimensionnelles.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLinesEvents>|Avertit les clients des modifications apportées à la mémoire tampon de texte sous-jacente sous forme de coordonnées à deux dimensions.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserDataEvents>|Avertit les clients des modifications apportées aux données utilisateur.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsPreliminaryTextChangeCommitEvents>|Avertit les clients du dernier mouvement de validation pour déclencher l'événement et fournit la plage de texte modifié. L' `IVsPreliminaryTextChangeCommitEvents` interface n’est pas déclenchée en réponse aux commandes d’annulation ou de rétablissement. Les événements se déclenchent uniquement pour les mémoires tampons qui disposent d’un gestionnaire d’annulation. `IVsPreliminaryTextChangeCommitEvents` est déclenché avant d’autres événements, tels que la liste pour s’assurer que les autres événements ne modifient pas le texte avant que les modifications ne soient validées. Votre VSPackage doit surveiller l' `IVsPreliminaryTextChangeCommitEvents` interface ou l' `IVsFinalTextChangeCommitEvents` interface, mais pas les deux.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsFinalTextChangeCommitEvents>|Avertit les clients du dernier mouvement de validation pour déclencher l'événement et fournit la plage de texte modifié. L' `IVsFinalTextChangeCommitEvents` interface n’est pas déclenchée en réponse aux commandes d’annulation ou de rétablissement. Les événements se déclenchent uniquement pour les mémoires tampons qui disposent d’un gestionnaire d’annulation. `IVsFinalTextChangeCommitEvents` est destiné à être utilisé uniquement par les services de langage ou d’autres objets qui ont un contrôle total sur la modification. Votre VSPackage doit surveiller l' `IVsPreliminaryTextChangeCommitEvents` interface ou l' `IVsFinalTextChangeCommitEvents` interface, mais pas les deux.|  
  
## <a name="see-also"></a>Voir aussi  
 [Accès à la mémoire tampon de texte à l’aide de l’API héritée](../extensibility/accessing-the-text-buffer-by-using-the-legacy-api.md)   
 [Guide pratique pour s’inscrire aux événements de mémoire tampon de texte avec l’API héritée](../extensibility/how-to-register-for-text-buffer-events-with-the-legacy-api.md)
