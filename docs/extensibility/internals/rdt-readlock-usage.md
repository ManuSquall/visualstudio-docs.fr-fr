---
title: Utilisation de RDT_ReadLock | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- RDT_ReadLock
- visible
- RDT_EditLock
- invisible
ms.assetid: b935fc82-9d6b-4a8d-9b70-e9a5c5ad4a55
caps.latest.revision: 8
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
ms.sourcegitcommit: e7575b914f0645882f3570bdbe29221f2f8130cc
ms.openlocfilehash: a8ea44ef2dea3b3c4ebd29cf95b1886e2028e2c3
ms.lasthandoff: 02/22/2017

---
# <a name="rdtreadlock-usage"></a>Utilisation de RDT_ReadLock

<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS>est un indicateur qui fournit la logique pour le verrouillage d’un document en l’exécutant Document Table d’exécution, qui est la liste de tous les documents actuellement ouverts dans l’IDE de Visual Studio.</xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS> Cet indicateur détermine quand les documents sont ouverts, et si le document est visible dans l’interface utilisateur ou stockées dans la mémoire de manière invisible.

En règle générale, vous utiliseriez <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS>lorsque un des éléments suivants est vrai :</xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS>

- Lorsque vous souhaitez ouvrir un document de façon transparente et en lecture seule, mais il n’est pas encore établie qui <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>doit appartenir à celui-ci.</xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>

- Lorsque vous souhaitez que l’utilisateur invité à enregistrer un document qui a été ouvert de façon invisible avant que l’utilisateur qu’il affiche dans l’interface utilisateur et a tenté de le fermer.

## <a name="how-to-manage-visible-and-invisible-documents"></a>Comment gérer les Documents visibles et invisibles

Lorsqu’un utilisateur ouvre un document dans l’interface utilisateur, un <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>propriétaire du document doit être établie et un <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS>indicateur doit être défini.</xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS> </xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> Si aucune <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>propriétaire peut être établi, puis le document n’est pas enregistré lorsque l’utilisateur clique sur **Enregistrer tout** ou ferme l’IDE.</xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> Cela signifie que si un document est ouvert de manière invisible lorsqu’il est modifié dans la mémoire, et l’utilisateur est invité à enregistrer le document lors de l’arrêt ou enregistré si **enregistrer tous les** est sélectionnée, alors un `RDT_ReadLock` ne peut pas être utilisé. Au lieu de cela, vous devez utiliser un `RDT_EditLock` et inscrire un <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder>lorsqu’un <xref:Microsoft.VisualStudio.Shell.Interop.__VSREGDOCLOCKHOLDER>indicateur.</xref:Microsoft.VisualStudio.Shell.Interop.__VSREGDOCLOCKHOLDER> </xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder>

## <a name="rdteditlock-and-document-modification"></a>RDT_EditLock et Modification de Document

L’indicateur précédent mentionné indique que l’ouverture du document invisible génère son `RDT_EditLock` lorsque le document est ouvert par l’utilisateur dans un visible **DocumentWindow**. Lorsque cela se produit, l’utilisateur voit s’afficher un **enregistrer** invite lorsque visibles **DocumentWindow** est fermé. <xref:Microsoft.VisualStudio.Package.Automation.OAProject.CodeModel>les implémentations qui utilisent la <xref:Microsoft.VisualStudio.Shell.Interop.IVsInvisibleEditorManager>service fonctionne initialement lorsque seul un `RDT_ReadLock` est effectuée (par exemple, lorsque le document est ouvert de manière invisible pour analyser les informations).</xref:Microsoft.VisualStudio.Shell.Interop.IVsInvisibleEditorManager></xref:Microsoft.VisualStudio.Package.Automation.OAProject.CodeModel> Plus tard, si le document doit être modifié, puis le verrou est mis à niveau vers un faible **RDT_EditLock**. Si l’utilisateur ouvre ensuite le document dans un **DocumentWindow**, le `CodeModel`de faible `RDT_EditLock` est libéré.

Si l’utilisateur ferme puis le **DocumentWindow** et choisit **non** lorsque vous êtes invité à enregistrer le document ouvert, puis la `CodeModel` implémentation supprime toutes les informations dans le document et rouvre le document à partir du disque de manière invisible la prochaine fois plus d’informations est requis pour le document. Les spécificités de ce comportement est une instance où l’utilisateur ouvre le **DocumentWindow** du document ouvert invisible, modifie, ferme et choisit ensuite **non** lorsque vous êtes invité à enregistrer le document. Dans ce cas, si le document a un `RDT_ReadLock`, le document n’est pas réellement fermé, puis le document modifié reste ouvert invisible dans la mémoire, même si l’utilisateur choisi de ne pas enregistrer le document.

Si l’ouverture du document invisible utilise un faible `RDT_EditLock`, puis il donne son verrou lorsque l’utilisateur ouvre le document visiblement et aucun autre des verrous. Lorsque l’utilisateur ferme le **DocumentWindow** et choisit **non** lorsque vous êtes invité à enregistrer le document, le document doit être fermé à partir de la mémoire. Cela signifie que le client invisible doit écouter les événements de r & DT à suivre cette occurrence. La prochaine fois que le document est requis, le document doit être rouvert.
