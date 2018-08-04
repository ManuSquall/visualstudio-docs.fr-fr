---
title: Chargement de Document différé | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: fb07b8e2-a4e3-4cb0-b04f-8eb11c491f35
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 03ca02010586711fa1a9af463f2fde5d0f4963a5
ms.sourcegitcommit: 1c2ed640512ba613b3bbbc9ce348e28be6ca3e45
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/03/2018
ms.locfileid: "39500366"
---
# <a name="delayed-document-loading"></a>Chargement de document différé
Lorsqu’un utilisateur ouvre de nouveau une solution Visual Studio, la plupart des documents associés n’est pas chargée immédiatement. Le frame de fenêtre de document est créé dans un état en attente de l’initialisation, et un document d’espace réservé (appelé un frame de stub) est placé dans la table de Document en cours d’exécution (RDT).  
  
Votre extension peut entraîner des documents de projet à charger inutilement en interrogeant les éléments dans les documents avant qu’ils sont chargés, ce qui peuvent augmenter l’encombrement de mémoire globale pour Visual Studio.  
  
## <a name="document-loading"></a>Chargement de document  
Le document et le frame de stub sont entièrement initialisées lorsque l’utilisateur accède au document, par exemple en sélectionnant l’onglet du frame de fenêtre. Le document peut également être initialisé par une extension qui demande des données du document, soit en accédant à la RDT directement pour acquérir les données de document, ou accéder à la table RDT indirectement en définissant un des appels suivants :  
  
- Le frame de fenêtre <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A> (méthode).  
  
- Le frame de fenêtre <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> méthode sur une des propriétés suivantes :  
  
   - <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
   - <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
   - <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
   - <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
   - <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
   - <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
- Si votre extension utilise du code managé, vous ne devez pas appeler <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.GetDocumentInfo%2A> , sauf si vous êtes certain que le document n’est pas dans l’état en attente de l’initialisation ou que vous souhaitez que le document soit entièrement initialisé. La raison est que la méthode retourne toujours la documentation de l’objet de données, créant si nécessaire. Au lieu de cela, vous devez appeler une des méthodes sur le `IVsRunningDocumentTable4` interface.  
  
- Si votre extension utilise C++, vous pouvez passer `null` pour les paramètres que vous ne souhaitez pas.  
  
- Vous pouvez éviter le chargement en appelant une des méthodes suivantes avant de lui demander pour les propriétés pertinentes avant de lui demander d’autres propriétés de document inutile :  
  
   - <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> à l’aide de <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID6>.  
  
   - <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentFlags%2A>. Cette méthode retourne un <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4> objet qui inclut une valeur pour <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4> si le document n’a pas encore été initialisé.  
  
Vous pouvez déterminer à quel moment un document a été chargé en vous abonnant à l’événement RDT qui est déclenché lorsqu’un document est entièrement initialisé. Il existe deux possibilités :  
  
- Si le récepteur d’événements implémente <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents2>, vous pouvez vous abonner à <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents2.OnAfterAttributeChangeEx%2A>,  
  
- Sinon, vous pouvez vous abonner à <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents.OnAfterAttributeChange%2A>.  
  

 L’exemple suivant est un scénario d’accès de document hypothétique : extension A Visual Studio souhaite afficher des informations sur les documents ouverts, par exemple la modification verrouiller les nombre et des informations sur les données du document. Il énumère les documents dans le RDT à l’aide <xref:Microsoft.VisualStudio.Shell.Interop.IEnumRunningDocuments>, puis appelle <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.GetDocumentInfo%2A> pour chaque document afin de récupérer les données de nombre et le document de verrouillage modifier. Si le document est dans l’état en attente de l’initialisation, qui demande les données de document fait à initialiser inutilement.  
  
 Un moyen plus efficace d’accéder à un document consiste à utiliser <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentEditLockCount%2A> pour obtenir le nombre de verrous de modification et puis <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentFlags%2A> pour déterminer si le document a été initialisé. Si les indicateurs n’incluent pas <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4>, le document a déjà été initialisé et qui demande les données de document avec <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentData%2A> n’entraîne pas de toute initialisation inutile. Si les indicateurs incluent <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4>, l’extension doit éviter de demander les données du document jusqu'à ce que le document est initialisé. Cette initialisation peut être détectée dans le `OnAfterAttributeChange(Ex)` Gestionnaire d’événements.  
  
## <a name="test-extensions-to-see-if-they-force-initialization"></a>Extensions pour voir si elles forcer l’initialisation de test  
 Il n’existe aucun indice visible pour indiquer si un document a été initialisé, il peut être difficile de savoir si votre extension est forçant. Vous pouvez définir une clé de Registre qui facilite la vérification, car elle force le titre de tous les documents qui ne sont pas entièrement initialisé pour que le texte *[Stub]* dans le titre.  
  
 Dans **HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\14.0\BackgroundSolutionLoad**, affectez la valeur **StubTabTitleFormatString** à  *{0} [Stub]*.