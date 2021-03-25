---
title: Chargement différé du document | Microsoft Docs
description: En savoir plus sur le chargement différé des documents dans Visual Studio et sur la façon de coder les extensions afin qu’elles ne interrogent pas les éléments d’un document avant qu’elle ne soit chargée.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: fb07b8e2-a4e3-4cb0-b04f-8eb11c491f35
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 959af31f1986a4ff670adc5d74573cfb2bb850ce
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105090981"
---
# <a name="delayed-document-loading"></a>Chargement différé du document

Quand un utilisateur ouvre à nouveau une solution Visual Studio, la plupart des documents associés ne sont pas chargés immédiatement. Le cadre de la fenêtre de document est créé dans un état d’initialisation en attente, et un document d’espace réservé (appelé frame de stub) est placé dans la table de document en cours d’exécution (RDT).

Votre extension peut entraîner le chargement inutile de documents de projet en interrogeant des éléments dans les documents avant leur chargement, ce qui peut augmenter l’encombrement mémoire global pour Visual Studio.

## <a name="document-loading"></a>Chargement de documents

Le frame et le document stub sont entièrement initialisés lorsque l’utilisateur accède au document, par exemple en sélectionnant l’onglet du cadre de la fenêtre. Le document peut également être initialisé par une extension qui demande les données du document, soit en accédant directement au RDT pour acquérir les données du document, soit en accédant indirectement à RDT en effectuant l’un des appels suivants :

- Méthode de frame de fenêtre <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A> .

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A>Méthode de frame de fenêtre sur l’une des propriétés suivantes :

  - [__VSFPROPID. VSFPROPID_DocView](<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID.VSFPROPID_DocView>)

  - [__VSFPROPID. VSFPROPID_ViewHelper](<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID.VSFPROPID_ViewHelper>)

  - [__VSFPROPID. VSFPROPID_DocData](<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID.VSFPROPID_DocData>)

  - [__VSFPROPID. VSFPROPID_AltDocData](<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID.VSFPROPID_AltDocData>)

  - [__VSFPROPID. VSFPROPID_RDTDocData](<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID.VSFPROPID_RDTDocData>)

  - [__VSFPROPID. VSFPROPID_SPProjContext](<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID.VSFPROPID_SPProjContext>)

- Si votre extension utilise du code managé, vous ne devez pas appeler, <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.GetDocumentInfo%2A> sauf si vous êtes certain que le document n’est pas dans l’état d’initialisation en attente, ou que vous souhaitez que le document soit entièrement initialisé. La raison est que la méthode retourne toujours l’objet de données de document, en le créant si nécessaire. Au lieu de cela, vous devez appeler l’une des méthodes sur l' `IVsRunningDocumentTable4` interface.

- Si votre extension utilise C++, vous pouvez transmettre `null` les paramètres que vous ne voulez pas.

- Vous pouvez éviter le chargement de documents inutiles en appelant l’une des méthodes suivantes avant de demander les propriétés appropriées avant de demander d’autres propriétés :

  - <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> utilisation de [__VSFPROPID6. VSFPROPID_PendingInitialization](<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID6.VSFPROPID_PendingInitialization>).

  - <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentFlags%2A>. Cette méthode retourne un <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4> objet qui comprend une valeur pour [_VSRDTFLAGS4. RDT_PendingInitialization](<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4.RDT_PendingInitialization>) si le document n’a pas encore été initialisé.

Vous pouvez déterminer quand un document a été chargé en s’abonnant à l’événement RDT qui est déclenché lorsqu’un document est entièrement initialisé. Il existe deux possibilités :

- Si le récepteur d’événements implémente <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents2> , vous pouvez vous abonner à <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents2.OnAfterAttributeChangeEx%2A> ,

- Dans le cas contraire, vous pouvez vous abonner à <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents.OnAfterAttributeChange%2A> .

L’exemple suivant est un scénario hypothétique d’accès aux documents : une extension Visual Studio souhaite afficher des informations sur les documents ouverts, par exemple le nombre de verrous de modification et une partie des données du document. Il énumère les documents dans le RDT à l’aide de <xref:Microsoft.VisualStudio.Shell.Interop.IEnumRunningDocuments> , puis appelle <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.GetDocumentInfo%2A> pour chaque document afin de récupérer le nombre de verrous de modification et les données de document. Si le document est dans l’état d’initialisation en attente, la demande des données du document provoque l’initialisation inutilement.

Un moyen plus efficace d’accéder à un document consiste à utiliser <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentEditLockCount%2A> pour obtenir le nombre de verrous de modification, puis <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentFlags%2A> à utiliser pour déterminer si le document a été initialisé. Si les indicateurs n’incluent pas [_VSRDTFLAGS4. RDT_PendingInitialization](<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4.RDT_PendingInitialization>), le document a déjà été initialisé et la demande des données de document avec <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentData%2A> n’entraîne pas d’initialisation inutile. Si les indicateurs incluent [_VSRDTFLAGS4. RDT_PendingInitialization](<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4.RDT_PendingInitialization>), l’extension doit éviter de demander les données de document jusqu’à ce que le document soit initialisé. Cette initialisation peut être détectée dans le `OnAfterAttributeChange(Ex)` Gestionnaire d’événements.

## <a name="test-extensions-to-see-if-they-force-initialization"></a>Tester les extensions pour déterminer si elles forcent l’initialisation

Il n’y a pas de signal visible pour indiquer si un document a été initialisé. il peut donc être difficile de déterminer si votre extension force l’initialisation. Vous pouvez définir une clé de Registre qui facilite la vérification, car elle provoque le titre de chaque document qui n’est pas entièrement initialisé pour avoir le texte *[stub]* dans le titre.

Dans **HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\14.0\BackgroundSolutionLoad**, définissez **StubTabTitleFormatString** sur *{0} [stub]*.
