---
title: Chargement de documents retardés (en anglais) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: fb07b8e2-a4e3-4cb0-b04f-8eb11c491f35
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2f78d49013c1f0bd359d4439b73620a159a9ccc0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708809"
---
# <a name="delayed-document-loading"></a>Chargement de documents retardé

Lorsqu’un utilisateur rouvre une solution Visual Studio, la plupart des documents associés ne sont pas chargés immédiatement. Le cadre de fenêtre de document est créé dans un état d’initialisation en attente, et un document de placeholder (appelé cadre de talon) est placé dans la table de document de fonctionnement (RDT).

Votre extension peut entraîner le chargement inutile de documents de projet en interrogeant des éléments dans les documents avant qu’ils ne soient chargés, ce qui peut augmenter l’empreinte mémoire globale de Visual Studio.

## <a name="document-loading"></a>Chargement de documents

Le cadre et le document du talon sont entièrement parasémentés lorsque l’utilisateur accède au document, par exemple en sélectionnant l’onglet du cadre de la fenêtre. Le document peut également être paralémenté par une extension qui demande les données du document, soit en accédant directement au RDT pour acquérir les données du document, soit en accédant indirectement au RDT en faisant l’un des appels suivants :

- La méthode <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A> du cadre de fenêtre.

- La méthode <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> du cadre de fenêtre sur l’une des propriétés suivantes :

  - [__VSFPROPID. VSFPROPID_DocView](<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID.VSFPROPID_DocView>)

  - [__VSFPROPID. VSFPROPID_ViewHelper](<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID.VSFPROPID_ViewHelper>)

  - [__VSFPROPID. VSFPROPID_DocData](<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID.VSFPROPID_DocData>)

  - [__VSFPROPID. VSFPROPID_AltDocData](<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID.VSFPROPID_AltDocData>)

  - [__VSFPROPID. VSFPROPID_RDTDocData](<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID.VSFPROPID_RDTDocData>)

  - [__VSFPROPID. VSFPROPID_SPProjContext](<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID.VSFPROPID_SPProjContext>)

- Si votre extension utilise le code <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.GetDocumentInfo%2A> géré, vous ne devez pas appeler sauf si vous êtes certain que le document n’est pas dans l’état d’initialisation en attente, ou vous voulez que le document soit entièrement initialisé. La raison en est que la méthode renvoie toujours l’objet de données doc, la créant si nécessaire. Au lieu de cela, vous `IVsRunningDocumentTable4` devriez appeler l’une des méthodes sur l’interface.

- Si votre extension utilise C, vous `null` pouvez passer pour les paramètres que vous ne voulez pas.

- Vous pouvez éviter le chargement inutile des documents en appelant l’une des méthodes suivantes avant de demander les propriétés pertinentes avant de demander d’autres propriétés :

  - <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A>l’utilisation [de __VSFPROPID6. VSFPROPID_PendingInitialization](<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID6.VSFPROPID_PendingInitialization>).

  - <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentFlags%2A>. Cette méthode <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4> renvoie un objet qui comprend une valeur pour [_VSRDTFLAGS4. RDT_PendingInitialization](<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4.RDT_PendingInitialization>) si le document n’a pas encore été paradé.

Vous pouvez savoir quand un document a été chargé en vous abonnant à l’événement RDT qui est soulevé lorsqu’un document est entièrement para initialisé. Il y a deux possibilités :

- Si l’évier <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents2>de l’événement <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents2.OnAfterAttributeChangeEx%2A>met en œuvre, vous pouvez vous abonner à ,

- Sinon, vous pouvez <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents.OnAfterAttributeChange%2A>vous abonner à .

L’exemple suivant est un scénario hypothétique d’accès au document : une extension visual Studio veut afficher certaines informations sur les documents ouverts, par exemple le nombre de verrous de modification et quelque chose sur les données du document. Il énumère les documents dans le <xref:Microsoft.VisualStudio.Shell.Interop.IEnumRunningDocuments>RDT <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.GetDocumentInfo%2A> à l’aide , puis appelle pour chaque document afin de récupérer le nombre de verrouillage de modification et les données de document. Si le document est dans l’état d’initialisation en attente, demander les données du document les rend inutilement initialisés.

Un moyen plus efficace d’accéder <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentEditLockCount%2A> à un document est d’utiliser pour obtenir le nombre de verrous de modification, puis utiliser <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentFlags%2A> pour déterminer si le document a été initialisé. Si les drapeaux n’incluent pas [_VSRDTFLAGS4. RDT_PendingInitialization](<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4.RDT_PendingInitialization>), le document a déjà été parasécé, <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentData%2A> et demander les données du document avec ne provoque pas d’initialisation inutile. Si les drapeaux comprennent [_VSRDTFLAGS4. RDT_PendingInitialization,](<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4.RDT_PendingInitialization>)l’extension doit éviter de demander les données du document jusqu’à ce que le document soit paradé. Cette initialisation peut être `OnAfterAttributeChange(Ex)` détectée dans le gestionnaire d’événements.

## <a name="test-extensions-to-see-if-they-force-initialization"></a>Prolongations de test pour voir si elles forcent l’initialisation

Il n’y a aucun indice visible pour indiquer si un document a été initialisé, de sorte qu’il peut être difficile de savoir si votre extension force l’initialisation. Vous pouvez définir une clé de registre qui facilite la vérification, car elle rend le titre de chaque document qui n’est pas entièrement paraséqué pour avoir le texte *[Stub]* dans le titre.

Dans **HKEY_CURRENT_USER-Software-Microsoft-VisualStudio-14.0-BackgroundSolutionLoad**, set **StubTabTitleFormatString** à * {0} [Stub]*.
