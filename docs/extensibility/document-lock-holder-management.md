---
title: Gestion des titulaires de verrous de documents | Microsoft Docs
description: Découvrez comment placer un verrou de modification sur un document dans la table de documents en cours d’exécution sans que l’utilisateur ne visualise un document ouvert dans une fenêtre de document.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - document locking
ms.assetid: fa1ce513-eb7d-42bc-b6e8-cb2433d051d5
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 88e66ed3b0a5434f4d875bf941e3eeffb8adc092
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105091186"
---
# <a name="document-lock-holder-management"></a>Gestion des titulaires de verrous de documents

La table de document en cours d’exécution (RDT) gère le nombre de documents ouverts et les éventuels verrous de modification dont ils disposent. Vous pouvez placer un verrou de modification sur un document dans le RDT lorsqu’il est modifié par programmation en arrière-plan sans que l’utilisateur ne voit un document ouvert dans une fenêtre de document. Cette fonctionnalité est souvent utilisée par les concepteurs qui modifient plusieurs fichiers par le biais d’une interface utilisateur graphique.

## <a name="document-lock-holder-scenarios"></a>Scénarios de détenteur de verrou de document

### <a name="file-a-has-a-dependence-on-file-b"></a>Le fichier « a » a une dépendance vis-à-vis du fichier « b »

Envisagez une situation où vous implémentez un éditeur standard « A » pour le type de fichier « a », et chaque fichier de type « a » fait référence à un fichier de type « b » (ou dépend de celui-ci). Un éditeur standard « B » existe pour les fichiers de type « b ». Lorsque l’éditeur « A » ouvre le fichier « a », il récupère la référence au fichier correspondant « b ». Le fichier « b » n’est pas affiché, mais l’éditeur « A » peut le modifier. L’éditeur « A » obtient une référence aux données de document du fichier « b » de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.FindAndLockDocument%2A> méthode et gère également un verrou de modification sur le fichier « b ». Une fois que l’éditeur « A » a terminé la modification du fichier « b », vous pouvez décrémenter le nombre de verrous de modification sur le fichier « b » en appelant la <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnlockDocument%2A> méthode. Vous pouvez omettre cette étape si vous aviez appelé la <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.FindAndLockDocument%2A> méthode avec le paramètre `dwRDTLockType` défini sur [_VSRDTFLAGS. RDT_NoLock](<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS.RDT_NoLock>).

### <a name="file-b-is-opened-by-a-different-editor"></a>Le fichier « b » est ouvert par un autre éditeur

Dans le cas où le fichier « b » est déjà ouvert par l’éditeur « B » lorsque l’éditeur « A » tente de l’ouvrir, deux scénarios distincts sont à prendre en compte :

- Si le fichier « b » est ouvert dans un éditeur compatible, vous devez disposer de l’éditeur « A » pour enregistrer un verrou de modification de document sur le fichier « b » à l’aide de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.RegisterDocumentLockHolder%2A> méthode. Une fois que l’éditeur « A » a fini de modifier le fichier « b », annulez l’enregistrement du verrou de modification de document à l’aide de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnregisterDocumentLockHolder%2A> méthode.

- Si le fichier « b » est ouvert de manière incompatible, vous pouvez laisser la tentative d’ouverture du fichier « b » par l’éditeur « A » échouer, ou vous pouvez laisser la vue associée à l’éditeur « A » partiellement ouverte et afficher un message d’erreur approprié. Le message d’erreur doit indiquer à l’utilisateur de fermer le fichier « b » dans l’éditeur incompatible, puis de rouvrir le fichier « a » à l’aide de l’éditeur « A ». Vous pouvez également implémenter la [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] méthode <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable2.QueryCloseRunningDocument%2A> pour inviter l’utilisateur à fermer le fichier « b » qui est ouvert dans l’éditeur incompatible. Si l’utilisateur ferme le fichier « b », l’ouverture du fichier « a » dans l’éditeur « A » se poursuit normalement.

## <a name="additional-document-edit-lock-considerations"></a>Considérations supplémentaires sur le verrou de modification de document

Vous bénéficiez d’un comportement différent si l’éditeur « A » est le seul éditeur ayant un verrou de modification de document sur le fichier « b » que vous le feriez si l’éditeur « B » contient également un verrou de modification de document sur le fichier « b ». Dans [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] , **Concepteur de classes** est un exemple de concepteur visuel qui ne contient pas de verrou de modification sur le fichier de code associé. Autrement dit, si l’utilisateur a un diagramme de classes ouvert en mode Design et que le fichier de code associé est ouvert simultanément, et si l’utilisateur modifie le fichier de code mais n’enregistre pas les modifications, les modifications sont également perdues dans le fichier du diagramme de classes (. CD). Si le **Concepteur de classes** a le seul verrou de modification de document sur le fichier de code, l’utilisateur n’est pas invité à enregistrer les modifications lors de la fermeture du fichier de code. L’IDE demande à l’utilisateur d’enregistrer les modifications uniquement après que l’utilisateur a fermé l' **Concepteur de classes**. Les modifications enregistrées sont reflétées dans les deux fichiers. Si les **Concepteur de classes** et l’éditeur de fichier de code contenaient des verrous de modification de document sur le fichier de code, l’utilisateur est invité à enregistrer lors de la fermeture du fichier de code ou du formulaire. À ce stade, les modifications enregistrées sont reflétées à la fois dans le formulaire et dans le fichier de code. Pour plus d’informations sur les diagrammes de classes, consultez [utiliser des diagrammes de classes (Concepteur de classes)](../ide/class-designer/designing-and-viewing-classes-and-types.md).

Notez que, si vous devez placer un verrou de modification sur un document pour un non-éditeur, vous devez implémenter l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder> interface.

Plusieurs fois qu’un concepteur d’interface utilisateur qui modifie des fichiers de code par programmation apporte des modifications à plusieurs fichiers. Dans ce cas, la <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell2.SaveItemsViaDlg%2A> méthode gère l’enregistrement d’un ou plusieurs documents au moyen de la boîte de dialogue voulez **-vous enregistrer les modifications apportées aux éléments suivants ?** .

## <a name="see-also"></a>Voir aussi

- [Table de document en cours d’exécution](../extensibility/internals/running-document-table.md)
- [Persistance et table de document en cours d’exécution](../extensibility/internals/persistence-and-the-running-document-table.md)
