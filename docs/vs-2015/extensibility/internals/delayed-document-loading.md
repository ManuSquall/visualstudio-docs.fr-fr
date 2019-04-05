---
title: Chargement de Document différé | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: fb07b8e2-a4e3-4cb0-b04f-8eb11c491f35
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e3f3948756022c71e54699822715cf9a5b6d7896
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58948241"
---
# <a name="delayed-document-loading"></a>Chargement de document différé
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Lorsqu’un utilisateur ouvre de nouveau une solution Visual Studio, la plupart des documents associés n’est pas chargée immédiatement. Le frame de fenêtre de document est créé dans un état en attente de l’initialisation, et un document d’espace réservé (appelé un frame de stub) est placé dans la Table de Document en cours d’exécution (RDT).  
  
 Votre extension peut entraîner des documents de projet à charger inutilement en interrogeant les éléments dans les documents avant leur chargement. Cela peut augmenter l’encombrement de mémoire globale pour Visual Studio.  
  
## <a name="document-loading"></a>Chargement de document  
 Le document et le frame de stub sont entièrement initialisées lorsque l’utilisateur accède au document, par exemple en sélectionnant l’onglet du frame de fenêtre. Le document peut également être initialisé par une extension qui demande des données du document, soit en accédant à la RDT directement pour acquérir les données de document, ou accéder à la table RDT indirectement en définissant un des appels suivants :  
  
- Le frame de fenêtre de la méthode show : <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A>.  
  
- Le frame de fenêtre méthode GetProperty <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> sur toutes les propriétés suivantes :  
  
  -   <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
  -   <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
  -   <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
  -   <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
  -   <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
  -   <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
  Si votre extension utilise du code managé, vous ne devez pas appeler <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.GetDocumentInfo%2A> , sauf si vous êtes certain que le document n’est pas dans l’état en attente de l’initialisation ou que vous souhaitez que le document soit entièrement initialisé pour... Il s’agit, car cette méthode retourne toujours la documentation de l’objet de données, créant si nécessaire. Au lieu de cela, vous devez appeler une des méthodes sur l’interface IVsRunningDocumentTable4.  
  
  Si votre extension utilise C++, vous pouvez passer `null` pour les paramètres que vous ne souhaitez pas.  
  
  Vous pouvez éviter le chargement du document inutiles en appelant une des méthodes suivantes avant de lui demander pour les propriétés pertinentes : avant de lui demander d’autres propriétés.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> à l’aide de <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID6>.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentFlags%2A>. Cette méthode retourne un <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4> objet qui inclut une valeur pour <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4> si le document n’a pas encore été initialisé.  
  
  Vous pouvez déterminer à quel moment un document a été chargé en vous abonnant à l’événement RDT qui est déclenché lorsqu’un document est entièrement initialisé. Il existe deux possibilités :  
  
- Si le récepteur d’événements implémente <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents2>, vous pouvez vous abonner à <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents2.OnAfterAttributeChangeEx%2A>,  
  
- Sinon, vous pouvez vous abonner à <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents.OnAfterAttributeChange%2A>.  
  
  Voici un scénario d’accès de document hypothétique. Visual Studio extension souhaitez afficher des informations sur les documents ouverts, par exemple la modification de verrouillage nombre et des informations sur les données du document. Il énumère les documents dans le RDT à l’aide <xref:Microsoft.VisualStudio.Shell.Interop.IEnumRunningDocuments>, puis appelle <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.GetDocumentInfo%2A> pour chaque document afin de récupérer les données de nombre et le document de verrouillage modifier. Si le document est dans l’état en attente de l’initialisation, qui demande les données de document fait à initialiser inutilement.  
  
  Un moyen plus efficace de cette opération consiste à utiliser <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentEditLockCount%2A> pour obtenir le nombre de verrous de modification et puis <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentFlags%2A> pour déterminer si le document a été initialisé. Si les indicateurs n’incluent pas <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4>, le document a déjà été initialisé et qui demande les données de document avec <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentData%2A> n’entraîne pas de toute initialisation inutile. Si les indicateurs incluent <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4>, l’extension doit éviter de demander les données du document jusqu'à ce que le document est initialisé. Cela peut être détectée dans le Gestionnaire d’événements OnAfterAttributeChange(Ex).  
  
## <a name="testing-extensions-to-see-if-they-force-initialization"></a>Extensions pour voir si elles forcer l’initialisation de test  
 Il n’existe aucun indice visible pour indiquer si un document a été initialisé, il peut être difficile de savoir si votre extension est forçant. Vous pouvez définir une clé de Registre qui facilite la vérification, car elle force le titre de tous les documents qui ne sont pas entièrement initialisé pour que le texte `[Stub]` dans le titre.  
  
 Dans **HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\14.0\BackgroundSolutionLoad]**, affectez la valeur **StubTabTitleFormatString** à  **{0} [Stub]**.
