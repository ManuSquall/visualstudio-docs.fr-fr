---
title: Table de documents en cours d’exécution | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- read locks
- running document table (RDT), IVsDocumentLockHolder interface
- running document table (RDT)
- running document table (RDT), edit locks
- document data objects, running document table
ms.assetid: bbec74f3-dd8e-48ad-99c1-2df503c15f5a
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 4a49a5267fcccbde60e194e3fc58b0f6b6ea7552
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="running-document-table"></a>Table de Document en cours d’exécution
L’IDE gère la liste de tous les documents actuellement ouverts dans une structure interne appelée table de document en cours d’exécution (r & DT). Cette liste inclut tous les documents ouverts dans la mémoire, indépendamment de si ces documents sont actuellement en cours de modification. Un document est n’importe quel élément est rendu persistant, y compris les fichiers dans un projet ou le fichier projet principal (par exemple, un fichier .vcxproj).  
  
## <a name="elements-of-the-running-document-table"></a>Éléments de la Table de Document en cours d’exécution  
 La table de document en cours d’exécution contient les entrées suivantes.  
  
|Élément|Description|  
|-------------|-----------------|  
|Moniker de document|Chaîne qui identifie de façon unique l’objet de données du document. Cela peut être le chemin d’accès absolu pour un système de projet qui gère les fichiers (par exemple, C:\MyProject\MyFile). Cette chaîne est également utilisée pour les projets enregistrés dans les magasins de systèmes de fichiers, tels que des procédures stockées dans une base de données. Dans ce cas, le système de projet d’inventer une chaîne unique qu’elle peut reconnaître et éventuellement analyser pour déterminer comment stocker le document.|  
|Propriétaire de la hiérarchie|L’objet de hiérarchie qui possède le document, comme représenté par un <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> interface.|  
|ID d’élément|Identificateur d’élément pour un élément spécifique dans la hiérarchie. Cette valeur est unique parmi tous les documents dans la hiérarchie auquel appartient ce document, mais cette valeur n’est pas garantie pour être unique au sein des hiérarchies différentes.|  
|Objet de données de document|Au minimum, il s’agit d’un `IUnknown`<br /><br /> . L’IDE ne nécessite pas de n’importe quelle interface particulier au-delà de la `IUnknown` interface pour l’objet de données de document d’un éditeur personnalisé. Toutefois, pour un éditeur standard, mise en œuvre de l’éditeur de le <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> interface est requise pour traiter des appels de persistance de fichier à partir du projet. Pour plus d’informations, consultez [enregistrer un Document Standard](../../extensibility/internals/saving-a-standard-document.md).|  
|Indicateurs|Indicateurs qui contrôlent si le document est enregistré, si un verrou de lecture ou de modification est appliqué et ainsi de suite, peuvent être spécifiés lorsque les entrées sont ajoutées à la r & DT. Pour plus d’informations, consultez l’énumération <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS>.|  
|Modifier le nombre de verrous|Nombre de verrous de modification. Un verrou de modification indique que certains éditeur a le document ouvrent pour être modifiées. Lorsque le nombre de verrous de modification passe à zéro, l’utilisateur est invité à enregistrer le document, s’il a été modifié. Par exemple, chaque fois que vous ouvrez un document dans un éditeur à l’aide de la **nouvelle fenêtre** de commande, un verrou de modification est ajouté pour ce document dans la r & DT. Dans l’ordre pour un verrou de modification à définir, le document doit avoir une hiérarchie ou ID d’élément|  
|Nombre de verrous de lecture|Nombre de verrous de lecture. Un verrou de lecture indique que le document en cours est en lecture via un mécanisme par exemple un Assistant. Un verrou de lecture conserve un document actif dans la r & DT en indiquant que le document ne peut pas être modifié. Vous pouvez définir un verrou de lecture même si le document ne pas avoir une hiérarchie ou ID d’élément Cette fonctionnalité vous permet d’ouvrir un document en mémoire et entrez dans la r & DT sans le document en cours appartenant à une hiérarchie. Cette fonctionnalité est rarement utilisée.|  
|Détenteur de verrou|Une instance d’un <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder> interface. Le détenteur du verrou est implémenté par les fonctionnalités telles que des Assistants qui ouvrent et modifier des documents en dehors d’un éditeur. Un détenteur de verrou permet à la fonctionnalité Ajouter un verrou de modification du document à empêcher que le document fermé tandis qu’il est toujours en cours de modification. Normalement, modifier les verrous sont uniquement ajoutées par les fenêtres de document (autrement dit, les éditeurs).|  
  
 Chaque entrée dans la r & DT a une hiérarchie unique ou un ID d’élément associé, qui correspond généralement à un seul nœud dans le projet. Tous les documents disponibles pour la modification appartiennent généralement à une hiérarchie. Les entrées effectuées dans la r & DT contrôlent quel projet, ou, plus précisément, quelle hiérarchie, actuellement propriétaire de l’objet de données de document en cours de modification. En utilisant les informations dans la r & DT, l’IDE peut empêcher un document qui est ouvert en plusieurs projets à la fois.  
  
 La hiérarchie de contrôle de la persistance des données et utilise les informations dans la r & DT pour mettre à jour le **enregistrer** et **Enregistrer sous** boîtes de dialogue. Lorsque les utilisateurs de modifier un document, puis le **quitter** commande à partir de la **fichier** menu, l’IDE les invite au **enregistrer les modifications** boîte de dialogue pour afficher tous les projets et les éléments de projet qui sont actuellement modifiés. Cela permet aux utilisateurs de choisir parmi les documents à enregistrer. La liste des documents à enregistrer (autrement dit, les documents qui ont des modifications) est généré à partir de la r & DT. Tous les éléments que vous attendez à voir dans le **enregistrer les modifications** boîte de dialogue en quittant l’application doit avoir des enregistrements dans la r & DT. La r & DT coordonne les documents sont enregistrés et si l’utilisateur est invité à propos d’un enregistrement opération en utilisant les valeurs spécifiées dans l’entrée d’indicateurs pour chaque document. Pour plus d’informations sur les indicateurs de r & DT, consultez le <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS> énumération.  
  
## <a name="edit-locks-and-read-locks"></a>Les verrous de modification et de lecture  
 Les verrous de modification et de lecture se trouvent dans la r & DT. Les incréments de fenêtre de document et décrémente la modification de verrouillage. Par conséquent, lorsqu’un utilisateur ouvre une nouvelle fenêtre de document, le modifier nombre de verrous par incréments d’une unité. Lorsque le nombre de verrous de modification atteint zéro, la hiérarchie est signalée pour la rendre persistante ou enregistrer les données pour le document associé. La hiérarchie peut puis conserve les données de quelque façon, y compris la persistance sous forme de fichier ou un élément dans un référentiel. Vous pouvez utiliser la <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.LockDocument%2A> méthode dans le <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable> interface pour ajouter des verrous de modification et de lire des verrous et le <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnlockDocument%2A> méthode pour supprimer ces verrous.  
  
 En règle générale, lorsque la fenêtre de document pour un éditeur est instanciée, le frame de fenêtre ajoute automatiquement un verrou de modification pour le document dans la r & DT. Toutefois, si vous créez une vue personnalisée d’un document qui n’utilise pas une fenêtre de document standard (autrement dit, il n’implémente pas le <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> interface), vous devez définir votre propre verrou de modification. Par exemple, dans un Assistant, un document est modifié sans être ouvert dans un éditeur. Pour les verrous de document à ouvrir par les Assistants et les entités similaires, ces entités doivent implémenter la <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder> interface. Pour inscrire votre détenteur du verrou de document, appelez le <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.RegisterDocumentLockHolder%2A> méthode et passer votre <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder> implémentation. Cela ajoute le détenteur du verrou document la r & DT. Un autre scénario d’implémentation d’un détenteur de verrou de document est si vous ouvrez un document dans une fenêtre outil spécial. Dans ce cas, vous ne pouvez pas avoir à la fenêtre outil de fermer le document. Toutefois, l’inscription d’un détenteur de verrou de document dans la r & DT, l’IDE permet d’appeler votre implémentation de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder.CloseDocumentHolder%2A> méthode pour demander une fermeture du document.  
  
## <a name="other-uses-of-the-running-document-table"></a>Autres utilisations de la Table de Document en cours d’exécution  
 D’autres entités de l’IDE utilisent la r & DT pour obtenir des informations sur les documents. Par exemple, le Gestionnaire de contrôle de code source utilise la r & DT pour indiquer au système pour recharger un document dans l’éditeur, une fois qu’il obtient la version la plus récente du fichier. Pour ce faire, le Gestionnaire de contrôle de code source recherche les fichiers dans la r & DT pour voir si un d'entre eux sont ouvert. Si elles sont alors que le Gestionnaire de contrôle de code source vérifie que la hiérarchie implémente la <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A> (méthode). Si le projet n’implémente pas le <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A> (méthode), puis la source de contrôle les vérifications de gestionnaire pour une implémentation de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.ReloadDocData%2A> méthode sur l’objet de données de document directement.  
  
 L’IDE utilise également la r & DT à resurface (amener au premier plan) un document ouvert, si un utilisateur demande à ce document. Pour plus d’informations, consultez [affichage des fichiers à l’aide de la commande fichier ouvrir](../../extensibility/internals/displaying-files-by-using-the-open-file-command.md). Pour déterminer si un fichier est ouvert dans la r & DT, effectuez les opérations suivantes.  
  
-   Requête pour le moniker de document (autrement dit, le chemin d’accès complet de documents) déterminer si l’élément est ouvert.  
  
-   Utilisez l’ID de hiérarchie ou un élément pour demander le système de projet pour le chemin d’accès complet de documents, puis recherchez l’élément dans la r & DT.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation de RDT_ReadLock](../../extensibility/internals/rdt-readlock-usage.md)   
 [Persistance et table de document en cours d’exécution](../../extensibility/internals/persistence-and-the-running-document-table.md)