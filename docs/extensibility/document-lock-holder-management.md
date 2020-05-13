---
title: Gestion des détenteurs de serrures de document (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - document locking
ms.assetid: fa1ce513-eb7d-42bc-b6e8-cb2433d051d5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f9dd520f8ad5cab1f0cfee890c4bcc388c204bb1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712123"
---
# <a name="document-lock-holder-management"></a>Gestion des détenteurs de verrouillage de document

Le tableau de documents en cours d’exécution (RDT) maintient un nombre de documents ouverts et tous les verrous de modification qu’ils ont. Vous pouvez placer un verrou de modification sur un document dans le RDT lorsqu’il est édité de manière programmatique en arrière-plan sans que l’utilisateur ne voie un document ouvert dans une fenêtre de document. Cette fonctionnalité est souvent utilisée par les concepteurs qui modifient plusieurs fichiers via une interface utilisateur graphique.

## <a name="document-lock-holder-scenarios"></a>Scénarios de porte-verrouillage de document

### <a name="file-a-has-a-dependence-on-file-b"></a>Fichier "a" a une dépendance sur le fichier "b"

Considérez une situation où vous implémentez un éditeur standard "A" pour le type de fichier "a", et chaque fichier de type "a" a une référence (ou dépendance à) un fichier de type "b". Un éditeur standard "B" existe pour les fichiers de type "b". Lorsque l’éditeur "A" ouvre le fichier "a", il récupère la référence au fichier correspondant "b". Fichier "b" n’est pas affiché, mais l’éditeur "A" peut le modifier. L’éditeur "A" obtient une référence aux données de <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.FindAndLockDocument%2A> document du fichier "b" de la méthode et maintient également un verrou de modification sur le fichier "b". Après l’éditeur "A" est fait la modification du fichier "b" vous pouvez <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnlockDocument%2A> décrmer le nombre de verrouillage de modification sur le fichier "b" en appelant la méthode. Vous pouvez omettre cette étape <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.FindAndLockDocument%2A> si vous `dwRDTLockType` aviez appelé la méthode avec le paramètre réglé pour [_VSRDTFLAGS. RDT_NoLock](<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS.RDT_NoLock>).

### <a name="file-b-is-opened-by-a-different-editor"></a>Fichier "b" est ouvert par un éditeur différent

Dans le cas où le fichier "b" est déjà ouvert par l’éditeur "B" lorsque l’éditeur "A" tente de l’ouvrir, il ya deux scénarios distincts à gérer:

- Si le fichier "b" est ouvert dans un éditeur compatible, vous devez avoir l’éditeur "A" enregistrer un verrou de modification de document sur le fichier "b" en utilisant la <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.RegisterDocumentLockHolder%2A> méthode. Une fois que votre éditeur "A" est fait modifier le fichier <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnregisterDocumentLockHolder%2A> "b", désinscrire le verrou de modification de document en utilisant la méthode.

- Si le fichier "b" est ouvert d’une manière incompatible, vous pouvez soit laisser la tentative d’ouverture du fichier "b" par l’éditeur "A" échouer, ou vous pouvez laisser la vue associée à l’éditeur "A" partiellement ouvert et afficher un message d’erreur approprié. Le message d’erreur doit demander à l’utilisateur de fermer le fichier "b" dans l’éditeur incompatible, puis rouvrir le fichier "a" en utilisant l’éditeur "A". Vous pouvez également [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable2.QueryCloseRunningDocument%2A> implémenter la méthode pour inciter l’utilisateur à fermer le fichier "b" qui est ouvert dans l’éditeur incompatible. Si l’utilisateur ferme le fichier "b", l’ouverture du fichier "a" dans l’éditeur "A" se poursuit normalement.

## <a name="additional-document-edit-lock-considerations"></a>D’autres considérations de verrouillage de modification de document

Vous obtenez un comportement différent si l’éditeur "A" est le seul éditeur qui a un verrou de modification de document sur le fichier "b" que vous le feriez si l’éditeur "B" détient également un verrou de modification de document sur le fichier "b". Dans [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], **Class Designer** est un exemple d’un concepteur visuel qui ne tient pas un verrou de modification sur le fichier de code associé. Autrement dit, si l’utilisateur a un diagramme de classe ouvert dans la vue de conception et le fichier de code associé ouvert simultanément, et si l’utilisateur modifie le fichier de code, mais n’enregistre pas les modifications, les modifications sont également perdues au diagramme de classe (.cd) fichier. Si le **concepteur de classe** a le seul verrou de modification de document sur le fichier de code, l’utilisateur n’est pas invité à enregistrer les modifications lors de la fermeture du fichier de code. L’IDE demande à l’utilisateur d’enregistrer les modifications seulement après que l’utilisateur ferme le **Concepteur de classe**. Les modifications enregistrées sont reflétées dans les deux fichiers. Si le **concepteur de classe** et l’éditeur de fichiers de code ont tenu des verrous de modification de documents sur le fichier de code, alors l’utilisateur est invité à enregistrer lors de la fermeture du fichier de code ou le formulaire. À ce stade, les modifications enregistrées sont reflétées à la fois dans le formulaire et le fichier de code. Pour plus d’informations sur les diagrammes de classe, voir [Work with class diagrams (Class Designer)](../ide/class-designer/designing-and-viewing-classes-and-types.md).

Notez que si vous avez besoin de placer un verrou de <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder> modification sur un document pour un non-éditeur, vous devez implémenter l’interface.

Plusieurs fois, un concepteur d’interface utilisateur qui modifie les fichiers de code programmatiquement apporte des modifications à plus d’un fichier. Dans de <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell2.SaveItemsViaDlg%2A> tels cas, la méthode gère l’enregistrement d’un ou de plusieurs documents au moyen de la **Voulez-vous enregistrer les modifications aux éléments suivants?** boîte de dialogue.

## <a name="see-also"></a>Voir aussi

- [Table de document de fonctionnement](../extensibility/internals/running-document-table.md)
- [Persistance et tableau de document en cours d’exécution](../extensibility/internals/persistence-and-the-running-document-table.md)
