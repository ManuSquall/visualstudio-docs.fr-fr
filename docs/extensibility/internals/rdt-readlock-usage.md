---
title: utilisation RDT_ReadLock Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- RDT_ReadLock
- visible
- RDT_EditLock
- invisible
ms.assetid: b935fc82-9d6b-4a8d-9b70-e9a5c5ad4a55
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fb897fab61e1e14b52863b5853748c685200d5ba
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705931"
---
# <a name="rdt_readlock-usage"></a>Utilisation de RDT_ReadLock

[_VSRDTFLAGS. RDT_ReadLock](<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS.RDT_ReadLock>) est un drapeau qui fournit la logique pour verrouiller un document dans la Table du Document De Fonctionnement (RDT), qui est la liste de tous les documents qui sont actuellement ouverts dans l’IDE Visual Studio. Ce drapeau détermine quand les documents sont ouverts, et si un document est visible dans l’interface utilisateur ou maintenu invisiblement dans la mémoire.

En général, vous utilisez [_VSRDTFLAGS. RDT_ReadLock](<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS.RDT_ReadLock>) lorsque l’un des éléments suivants est vrai:

- Vous voulez ouvrir un document invisiblement et lu seulement, mais <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> il n’est pas encore établi qui devrait en être propriétaire.

- Vous souhaitez que l’utilisateur soit invité à enregistrer un document qui a été ouvert invisiblement avant que l’utilisateur ne l’affiche dans l’interface utilisateur, puis tente de le fermer.

## <a name="how-to-manage-visible-and-invisible-documents"></a>Comment gérer les documents visibles et invisibles

Lorsqu’un utilisateur ouvre un document <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> dans l’interface utilisateur, un propriétaire du document doit être établi et un [_VSRDTFLAGS. RDT_EditLock](<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS.RDT_EditLock>) drapeau doit être fixé. Si <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> aucun propriétaire ne peut être établi, le document ne sera pas enregistré lorsque l’utilisateur clique **sur Enregistrer tous** ou ferme l’IDE. Cela signifie que si un document est ouvert invisiblement lorsqu’il est modifié dans la mémoire, et que l’utilisateur est invité à enregistrer le document à l’arrêt ou à enregistrer si **Save All** est choisi, alors un `RDT_ReadLock` ne peut pas être utilisé. Au lieu de `RDT_EditLock` cela, <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder> vous devez utiliser un et enregistrer un quand un [__VSREGDOCLOCKHOLDER. RDLH_WeakLockHolder](<xref:Microsoft.VisualStudio.Shell.Interop.__VSREGDOCLOCKHOLDER.RDLH_WeakLockHolder>) drapeau.

## <a name="rdt_editlock-and-document-modification"></a>RDT_EditLock et modification de documents

Le drapeau précédent mentionné indique que l’ouverture `RDT_EditLock` invisible du document lui donnera lorsque le document sera ouvert par l’utilisateur dans un **DocumentWindow**visible . Lorsque cela se produit, l’utilisateur est présenté avec une invite **Enregistrer** lorsque le **DocumentWindow** visible est fermé. `Microsoft.VisualStudio.Package.Automation.OAProject.CodeModel`les implémentations qui utilisent le <xref:Microsoft.VisualStudio.Shell.Interop.IVsInvisibleEditorManager> service fonctionnent d’abord lorsqu’une seule est prise (c.-à-d. `RDT_ReadLock` lorsque le document est ouvert invisiblement pour analyser l’information). Plus tard, si le document doit être modifié, alors le verrou est mis à niveau vers une **RDT_EditLock**faible . Si l’utilisateur ouvre alors le document dans `CodeModel`un `RDT_EditLock` **DocumentWindow**visible , le «faible est libéré.

Si l’utilisateur ferme alors le **DocumentWindow** et choisit **Non** lorsqu’on lui demande d’enregistrer le document ouvert, alors la `CodeModel` mise en œuvre dispose de toutes les informations contenues dans le document et rouvre le document à partir du disque invisiblement la prochaine fois que plus d’informations sont nécessaires pour le document. La subtilité de ce comportement est un cas où l’utilisateur ouvre le **DocumentWindow** du document ouvert invisible, le modifie, le ferme, puis choisit **Non** lorsqu’on lui demande de sauver le document. Dans ce cas, si `RDT_ReadLock`le document a un , alors le document ne sera pas réellement fermé et le document modifié restera ouvert invisiblement dans la mémoire, même si l’utilisateur a choisi de ne pas enregistrer le document.

Si l’ouverture invisible du `RDT_EditLock`document utilise un faible, alors il cède son verrou lorsque l’utilisateur ouvre le document visiblement et aucun autre verrou n’est tenu. Lorsque l’utilisateur ferme le **DocumentWindow** et choisit **Non** lorsqu’on lui invite à enregistrer le document, le document doit être fermé de mémoire. Cela signifie que le client invisible doit écouter les événements RDT pour suivre cet événement. La prochaine fois que le document est requis, le document doit être rouvert.
