---
title: "Verrou détenteur de la gestion de documents | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], custom - document locking
ms.assetid: fa1ce513-eb7d-42bc-b6e8-cb2433d051d5
caps.latest.revision: 21
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
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: a78ee74a210f544ad4f9d97a9d2457bdf9d70988
ms.lasthandoff: 02/22/2017

---
# <a name="document-lock-holder-management"></a>Gestion de détenteur de verrouillage de document
La Table de Document en cours d’exécution (r & DT) conserve un décompte des documents ouverts et les verrous de modification qu’ils ont. Vous pouvez placer un verrou de modification d’un document dans la r & DT cas de modification par programme en arrière-plan sans que l’utilisateur d’afficher un document ouvert dans une fenêtre de document. Cette fonctionnalité est souvent utilisée par les concepteurs qui modifient plusieurs fichiers via une interface utilisateur graphique.  
  
## <a name="document-lock-holder-scenarios"></a>Scénarios de détenteur de verrouillage de document  
  
### <a name="file-a-has-a-dependence-on-file-b"></a>Fichier « a » une dépendance sur le fichier a « b »  
 Imaginons une situation où vous devez implémenter un éditeur standard « A » pour le type de fichier « a » et chaque fichier de type « a » a une référence à (ou une dépendance) un fichier du type « b ». Il existe un éditeur standard « B » pour les fichiers de type « b ». Lorsque l’éditeur « A » ouvre le fichier « a » il récupère la référence au fichier correspondant « b ». Le fichier « b » n’est pas affiché, mais « A » de l’éditeur peut le modifier. Éditeur de « A » Obtient une référence aux données de document du fichier « b » à partir de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.FindAndLockDocument%2A>méthode et gère également un verrou de modification sur le fichier « b ».</xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.FindAndLockDocument%2A> Éditeur « A » après modification du fichier « b », vous pouvez décrémenter le verrou de modification compter sur fichier « b » en appelant le <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnlockDocument%2A>méthode.</xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnlockDocument%2A> Vous pouvez omettre cette étape si vous aviez appelé le <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.FindAndLockDocument%2A>méthode avec le paramètre `dwRDTLockType` définie sur <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS>.</xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS> </xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.FindAndLockDocument%2A>  
  
### <a name="file-b-is-opened-by-a-different-editor"></a>Le fichier « b » est ouvert par un autre éditeur  
 Dans le cas où le fichier « b » est déjà ouvert par un éditeur « B » lorsque « A » de l’éditeur tente d’ouvrir, il existe deux scénarios distincts pour gérer :  
  
-   Si le fichier « b » est ouvert dans un éditeur compatible, vous devez disposer l’éditeur « A » inscrire un verrou de modification de document sur le fichier « b » à l’aide du <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.RegisterDocumentLockHolder%2A>méthode.</xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.RegisterDocumentLockHolder%2A> Issue de votre éditeur de « A » modification fichier « b », désenregistrez le document modifier à l’aide de verrouillage la <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnregisterDocumentLockHolder%2A>méthode.</xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnregisterDocumentLockHolder%2A>  
  
-   Si le fichier « b » est ouvert de manière incompatible, vous pouvez laisser l’ouverture du fichier « b » a été lancée par l’éditeur « A » échouent, ou vous pouvez laisser la vue associée à l’éditeur « A » est partiellement ouvre et affiche un message d’erreur approprié. Le message d’erreur doit indiquer à l’utilisateur de fermer le fichier « b » dans l’éditeur incompatible et ouvrez de nouveau fichier « a » à l’aide de l’éditeur « A ». Vous pouvez également implémenter le [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] méthode <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable2.QueryCloseRunningDocument%2A>pour inviter l’utilisateur à fermer le fichier « b » qui est ouvert dans l’éditeur incompatible.</xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable2.QueryCloseRunningDocument%2A> Si l’utilisateur ferme le fichier « b », l’ouverture du fichier « a » en « A » l’éditeur se poursuit normalement.  
  
## <a name="additional-document-edit-lock-considerations"></a>Considérations de verrouillage modifier documents supplémentaires  
 Vous obtenez un comportement différent si l’éditeur « A » est le seul éditeur qui a un document à modifier le verrou sur le fichier « b » que vous le feriez si l’éditeur « B » conserve également un document edit verrou sur le fichier « b ». Dans [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], **le Concepteur de classes** est un exemple d’un concepteur visuel qui ne possède pas un verrou de modification du fichier de code associé. Autrement dit, si l’utilisateur a un diagramme de classes ouvert en mode Design et le fichier de code associé ouverts simultanément, et si l’utilisateur modifie le fichier de code, mais ne pas enregistre les modifications, les modifications sont également perdues dans le fichier de diagramme (.cd) classe. Si le **le Concepteur de classes** est le seul document modifier un verrou sur le fichier de code, l’utilisateur n’est pas invité à enregistrer les modifications lors de la fermeture du fichier de code. L’IDE invite l’utilisateur à enregistrer les modifications uniquement une fois que l’utilisateur ferme le **le Concepteur de classes**. Les modifications enregistrées sont répercutées dans les deux fichiers. Si les deux le **le Concepteur de classes** et l’éditeur de fichier de code maintenu verrous de modification de document sur le fichier de code, puis l’utilisateur est invité à enregistrer lors de la fermeture de l’écran ou le fichier de code. À ce stade, les modifications enregistrées sont répercutées dans le formulaire et le fichier de code. Pour plus d’informations sur les diagrammes de classes, consultez [utilisation des diagrammes de classes (Concepteur de classes)](../ide/working-with-class-diagrams-class-designer.md).  
  
 Notez que si vous avez besoin de placer un verrou de modification sur un document pour un éditeur-non, vous devez implémenter le <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder>interface.</xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder>  
  
 Nombre de fois où un concepteur d’interface utilisateur qui modifie les fichiers de code par programme apporte des modifications à plusieurs fichiers. Dans ce cas la <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell2.SaveItemsViaDlg%2A>méthode gère l’enregistrement d’un ou plusieurs documents au moyen de la **vous souhaitez enregistrer les modifications apportées aux éléments suivants ?** boîte de dialogue.</xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell2.SaveItemsViaDlg%2A>  
  
## <a name="see-also"></a>Voir aussi  
 [Table de Document en cours d’exécution](../extensibility/internals/running-document-table.md)   
 [Persistance et la Table de Document en cours d’exécution](../extensibility/internals/persistence-and-the-running-document-table.md)
