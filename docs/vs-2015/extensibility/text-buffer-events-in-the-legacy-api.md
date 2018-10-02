---
title: Événements de mémoire tampon de texte dans l’API héritée | Microsoft Docs
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
- editors [Visual Studio SDK], legacy - text buffer events
ms.assetid: 9be49e9f-1864-41c2-8a3c-f66895881341
caps.latest.revision: 17
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 799443f4674c48201a161dbbd02d525afdb3218c
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47506236"
---
# <a name="text-buffer-events-in-the-legacy-api"></a>Événements de mémoire tampon de texte dans l’API héritée
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [événements de mémoire tampon de texte dans l’API héritée](https://docs.microsoft.com/visualstudio/extensibility/text-buffer-events-in-the-legacy-api).  
  
L’objet de mémoire tampon de texte émet plusieurs événements différents qui vous permettent de répondre à différentes situations.  
  
 Lorsque vous utilisez l’API héritée, vous devez implémenter les interfaces suivantes afin de recevoir des notifications de modification de la mémoire tampon de texte. Exposer les interfaces de la mémoire tampon de texte en utilisant le `IConnectionPointContainer` modifications de l’interface sur la mémoire tampon pour recevoir une notification de ligne à partir de la mémoire tampon. Pour plus d’informations, consultez [Comment : s’inscrire aux événements de mémoire tampon de texte avec l’API héritée](../extensibility/how-to-register-for-text-buffer-events-with-the-legacy-api.md). Dans le cas de `IVsTextStreamEvents` ou `IVsTextLinesEvents` interfaces, les modifications sont retournées dans l’une ou deux dimensions coordonnées, respectivement.  
  
## <a name="text-buffer-interfaces"></a>Interfaces de mémoire tampon de texte  
 Voici les interfaces implémentées par l’objet de mémoire tampon de texte.  
  
|Interface|Description|  
|---------------|-----------------|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompoundAction>|Permet la création d’actions composites (autrement dit, les actions qui sont regroupées dans une unité d’annulation/de rétablissement unique).|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData>|Active la persistance des données de document gérées par la mémoire tampon de texte.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>|Fournit des services de base ; utilisé par de nombreux clients.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>|Fournit lire et écrire des fonctionnalités à l’aide de coordonnées à deux dimensions. Hérite de `IVsTextBuffer`.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextScanner>|Offre un accès séquentiel, orienté flux et à du texte dans la mémoire tampon rapide.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream>|Fournit lire et écrire des fonctionnalités à l’aide des coordonnées unidimensionnelles. Hérite de `IVsTextBuffer`.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserData>|Fournit l’accès à une collection générique de propriétés. La propriété la plus importante est le nom ou le moniker, de la mémoire tampon. Vous pouvez stocker vos propres données aléatoires dans la mémoire tampon avec cette interface par la création d’un GUID et l’utiliser en tant que clé.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>|Prend en charge les points de connexion pour les événements.|  
  
## <a name="text-buffer-event-interfaces"></a>Interfaces d’événement de mémoire tampon de texte  
 Voici les interfaces pour la notification d’événement de mémoire tampon de texte.  
  
|Interface|Description|  
|---------------|-----------------|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferEvents>|Avertit les clients lorsqu’un nouveau service de langage est associé à une mémoire tampon de texte.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferDataEvents>|Avertit les clients lors de la mémoire tampon de texte est initialisée et lorsque des modifications sont apportées aux données dans la mémoire tampon de texte.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStreamEvents>|Avertit les clients des modifications apportées à la mémoire tampon sous-jacente dans les coordonnées unidimensionnelles.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLinesEvents>|Avertit les clients des modifications apportées à la mémoire tampon sous-jacente dans les coordonnées à deux dimensions.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserDataEvents>|Avertit les clients des modifications apportées aux données de l’utilisateur.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsPreliminaryTextChangeCommitEvents>|Avertit les clients du dernier mouvement de validation pour déclencher l’événement et fournit la plage de texte modifié. Le `IVsPreliminaryTextChangeCommitEvents` interface n’est pas déclenchée en réponse à annuler ou rétablir les commandes. Événements se déclenchent uniquement pour les mémoires tampons qui ont un gestionnaire d’annulation. `IVsPreliminaryTextChangeCommitEvents` est déclenché avant les autres événements, tels que de tabulation, afin de vous assurer que les autres événements ne modifient pas le texte avant que les modifications soient validées. Votre VSPackage doit surveiller un le `IVsPreliminaryTextChangeCommitEvents` interface ou le `IVsFinalTextChangeCommitEvents` interface, mais pas les deux.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsFinalTextChangeCommitEvents>|Avertit les clients du dernier mouvement de validation pour déclencher l’événement et fournit la plage de texte modifié. Le `IVsFinalTextChangeCommitEvents` interface n’est pas déclenchée en réponse à annuler ou rétablir les commandes. Événements se déclenchent uniquement pour les mémoires tampons qui ont un gestionnaire d’annulation. `IVsFinalTextChangeCommitEvents` est destiné uniquement par les services de langage ou d’autres objets qui ont un contrôle complet sur la modification. Votre VSPackage doit surveiller un le `IVsPreliminaryTextChangeCommitEvents` interface ou le `IVsFinalTextChangeCommitEvents` interface, mais pas les deux.|  
  
## <a name="see-also"></a>Voir aussi  
 [L’accès à la mémoire tampon de texte à l’aide de l’API héritée](../extensibility/accessing-the-text-buffer-by-using-the-legacy-api.md)   
 [Guide pratique pour s’inscrire aux événements de mémoire tampon de texte avec l’API héritée](../extensibility/how-to-register-for-text-buffer-events-with-the-legacy-api.md)

