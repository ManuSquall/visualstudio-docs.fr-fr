---
title: Chargement différé du document | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: fb07b8e2-a4e3-4cb0-b04f-8eb11c491f35
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 5565749a21614bb0b882beab8c83ed63bc839229
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68196870"
---
# <a name="delayed-document-loading"></a>Chargement de document différé
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Quand un utilisateur ouvre à nouveau une solution Visual Studio, la plupart des documents associés ne sont pas chargés immédiatement. Le cadre de la fenêtre de document est créé dans un état d’initialisation en attente, et un document d’espace réservé (appelé frame de stub) est placé dans la table de document en cours d’exécution (RDT).  
  
 Votre extension peut entraîner le chargement inutile de documents de projet en interrogeant des éléments dans les documents avant leur chargement. Cela peut augmenter l’encombrement mémoire global pour Visual Studio.  
  
## <a name="document-loading"></a>Chargement de documents  
 Le frame et le document stub sont entièrement initialisés lorsque l’utilisateur accède au document, par exemple en sélectionnant l’onglet du cadre de la fenêtre. Le document peut également être initialisé par une extension qui demande les données du document, soit en accédant directement au RDT pour acquérir les données du document, soit en accédant indirectement à RDT en effectuant l’un des appels suivants :  
  
- Méthode Show du frame de fenêtre : <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A> .  
  
- La méthode de frame de fenêtre GetProperty <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> sur l’une des propriétés suivantes :  
  
  - <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
  - <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
  - <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
  - <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
  - <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
  - <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
  Si votre extension utilise du code managé, vous ne devez pas appeler, <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.GetDocumentInfo%2A> sauf si vous êtes certain que le document n’est pas dans l’état d’initialisation en attente, ou que vous souhaitez que le document soit entièrement initialisé. Cela est dû au fait que cette méthode retourne toujours l’objet de données de document, en le créant si nécessaire. Au lieu de cela, vous devez appeler l’une des méthodes sur l’interface IVsRunningDocumentTable4.  
  
  Si votre extension utilise C++, vous pouvez transmettre `null` les paramètres que vous ne voulez pas.  
  
  Vous pouvez éviter le chargement de documents inutiles en appelant l’une des méthodes suivantes avant de demander les propriétés appropriées : avant de demander d’autres propriétés.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> à l’aide de <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID6> .  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentFlags%2A>. Cette méthode retourne un <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4> objet qui inclut une valeur pour <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4> si le document n’a pas encore été initialisé.  
  
  Vous pouvez déterminer quand un document a été chargé en s’abonnant à l’événement RDT qui est déclenché lorsqu’un document est entièrement initialisé. Il existe deux possibilités :  
  
- Si le récepteur d’événements implémente <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents2> , vous pouvez vous abonner à <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents2.OnAfterAttributeChangeEx%2A> ,  
  
- Dans le cas contraire, vous pouvez vous abonner à <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents.OnAfterAttributeChange%2A> .  
  
  Voici un scénario hypothétique d’accès aux documents. Une extension Visual Studio souhaite afficher des informations sur les documents ouverts, par exemple le nombre de verrous de modification et une partie des données du document. Il énumère les documents dans le RDT à l’aide de <xref:Microsoft.VisualStudio.Shell.Interop.IEnumRunningDocuments> , puis appelle <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.GetDocumentInfo%2A> pour chaque document afin de récupérer le nombre de verrous de modification et les données de document. Si le document est dans l’état d’initialisation en attente, la demande des données du document provoque l’initialisation inutilement.  
  
  Une méthode plus efficace consiste à utiliser <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentEditLockCount%2A> pour obtenir le nombre de verrous de modification, puis à utiliser <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentFlags%2A> pour déterminer si le document a été initialisé. Si les indicateurs n’incluent pas <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4> , le document a déjà été initialisé et la demande des données de document avec <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentData%2A> n’entraîne pas d’initialisation inutile. Si les indicateurs incluent <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4> , l’extension doit éviter de demander les données du document jusqu’à ce que le document soit initialisé. Cela peut être détecté dans le gestionnaire d’événements OnAfterAttributeChange (ex).  
  
## <a name="testing-extensions-to-see-if-they-force-initialization"></a>Test des extensions pour voir si elles forcent l’initialisation  
 Il n’y a pas de signal visible pour indiquer si un document a été initialisé. il peut donc être difficile de déterminer si votre extension force l’initialisation. Vous pouvez définir une clé de Registre qui facilite la vérification, car elle provoque le titre de chaque document qui n’est pas entièrement initialisé pour contenir le texte `[Stub]` dans le titre.  
  
 Dans **HKEY_CURRENT_USER \software\microsoft\visualstudio\14.0\backgroundsolutionload]**, définissez **StubTabTitleFormatString** sur ** {0} [stub]**.
