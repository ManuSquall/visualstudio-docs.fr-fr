---
title: "Table de Document en cours d’ex&#233;cution | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "verrous en lecture"
  - "table de document en cours d’exécution (r & DT), la IVsDocumentLockHolder interface"
  - "table de document en cours d’exécution (r & DT)"
  - "table document en cours d’exécution (r & DT), les verrous de modification"
  - "objets de données de document, table de document en cours d’exécution"
ms.assetid: bbec74f3-dd8e-48ad-99c1-2df503c15f5a
caps.latest.revision: 18
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 18
---
# Table de Document en cours d’ex&#233;cution
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

L’IDE gère la liste de tous les documents actuellement ouverts dans une structure interne appelée table de document en cours d’exécution \(r & DT\). Cette liste inclut tous les documents ouverts en mémoire, indépendamment de si ces documents sont en cours de modification. Un document est un élément qui est rendu persistant, y compris les fichiers dans un projet ou le fichier de projet principal \(par exemple, un fichier .vcxproj\).  
  
## Éléments de la Table de Document en cours d’exécution  
 La table de document en cours d’exécution contient les entrées suivantes.  
  
|Élément|Description|  
|-------------|-----------------|  
|Moniker de document|Chaîne qui identifie de façon unique l’objet de données de document. Il s’agit du chemin d’accès absolu d’un système de projet qui gère les fichiers \(par exemple, C:\\MyProject\\MyFile\). Cette chaîne est également utilisée pour les projets enregistrés dans des magasins de systèmes de fichiers, tels que des procédures stockées dans une base de données. Dans ce cas, le système de projet d’inventer une chaîne unique qu’il peut reconnaître et éventuellement analyser pour déterminer comment stocker le document.|  
|Propriétaire de la hiérarchie|L’objet de hiérarchie qui possède le document, tel que représenté par une <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> interface.|  
|ID de l’élément|Identificateur pour un élément spécifique dans la hiérarchie. Cette valeur est unique parmi tous les documents dans la hiérarchie auquel appartient ce document, mais cette valeur n’est pas garantie pour être unique au sein de différentes hiérarchies.|  
|Objet de données de document|Au minimum, il s’agit d’une `IUnknown`<br /><br /> . L’IDE ne nécessite pas de n’importe quelle interface particulier au\-delà de la `IUnknown` interface pour l’objet de données de document d’un éditeur personnalisé. Toutefois, pour un éditeur standard, mise en œuvre de l’éditeur de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> interface est requise pour traiter les appels de persistance de fichier du projet. Pour plus d'informations, consultez [Enregistrement d'un Document Standard](../../extensibility/internals/saving-a-standard-document.md).|  
|Indicateurs|Indicateurs qui contrôlent si le document est enregistré, si un verrou en lecture ou modification est appliqué et ainsi de suite, peuvent être spécifiés lorsque les entrées sont ajoutées à la r & DT. Pour plus d’informations, consultez la <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS> énumération.|  
|Modifier le nombre de verrous|Nombre de verrous de modification. Un verrou de modification indique que tout éditeur a le document ouvert pour la modification. Lorsque le nombre de verrous de modification passe à zéro, l’utilisateur est invité à enregistrer le document, s’il a été modifié. Par exemple, chaque fois que vous ouvrez un document dans un éditeur à l’aide de la **nouvelle fenêtre** de commande, un verrou de modification est ajouté pour ce document dans la r & DT. Dans l’ordre pour un verrou de modification à définir, le document doit avoir une hiérarchie ou ID d’élément|  
|Nombre de verrous en lecture|Nombre de verrous en lecture. Un verrou en lecture indique que le document est lu via un mécanisme par exemple un Assistant. Un verrou de lecture conserve un document actif dans la r & DT en indiquant que le document ne peut pas être modifié. Vous pouvez définir un verrou en lecture même si le document n’est pas une hiérarchie ou ID d’élément Cette fonctionnalité vous permet d’ouvrir un document en mémoire et entrez\-la dans la r & DT sans le document en cours appartient à une hiérarchie. Cette fonctionnalité est rarement utilisée.|  
|Détenteur de verrou|Une instance d’un <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder> interface. Le détenteur du verrou est implémenté par des fonctionnalités telles que des Assistants qui ouvrant et modifier des documents en dehors d’un éditeur. Un support de verrouillage permet à la fonctionnalité Ajouter un verrou de modification du document à empêcher que le document est fermé alors qu’il est en cours de modification. Éditez normalement, les verrous sont uniquement ajoutées par les fenêtres de document \(autrement dit, les éditeurs\).|  
  
 Chaque entrée dans la r & DT possède une hiérarchie unique ou l’ID de l’élément associé, qui correspond généralement à un seul nœud dans le projet. Disponible pour la modification de tous les documents sont généralement détenus par une hiérarchie. Contrôlent les entrées effectuées dans la r & DT le projet, ou, plus précisément, quelle hiérarchie, actuellement propriétaire de l’objet de données de document en cours de modification. En utilisant les informations dans la r & DT, l’IDE peut empêcher un document qui est ouvert en plusieurs projets à la fois.  
  
 La hiérarchie de contrôle de la persistance des données et utilise les informations de la r & DT pour mettre à jour le **Enregistrer** et **Enregistrer en tant que** boîtes de dialogue. Lorsque les utilisateurs de modifier un document, puis le **Exit** commande à partir de la **fichier** menu, l’IDE les invite au **Enregistrer les modifications** boîte de dialogue pour afficher tous les projets et éléments de projet qui sont actuellement modifiées. Cela permet aux utilisateurs de choisir parmi les documents à enregistrer. La liste des documents à enregistrer \(autrement dit, les documents contenant des modifications\) est généré à partir de la r & DT. Tous les éléments que vous attendez à voir dans le **Enregistrer les modifications** boîte de dialogue en quittant l’application doit avoir des enregistrements dans la r & DT. La r & DT coordonne les documents sont enregistrés et si l’utilisateur est invité sur un enregistrement opération en utilisant les valeurs spécifiées dans l’entrée d’indicateurs pour chaque document. Pour plus d’informations sur les indicateurs de r & DT, consultez le <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS> énumération.  
  
## Verrous de modification et de lecture  
 Verrous de modification et de lecture se trouvent dans la r & DT. Les incréments de fenêtre de document et décrémente la modification verrouiller. Ainsi, lorsqu’un utilisateur ouvre une nouvelle fenêtre de document, le verrou de modification nombre s’incrémente d’une unité. Lorsque le nombre de verrous de modification atteint zéro, la hiérarchie est signalée à conserver ou à enregistrer les données pour le document associé. La hiérarchie peut puis conserve les données de quelque façon, y compris la persistance sous forme de fichier ou un élément dans un référentiel. Vous pouvez utiliser la <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.LockDocument%2A> méthode dans le <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable> interface pour ajouter des verrous de modification et les verrous en lecture et le <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnlockDocument%2A> méthode pour supprimer ces verrous.  
  
 En règle générale, lorsque la fenêtre de document pour un éditeur est instanciée, le frame de fenêtre ajoute automatiquement un verrou de modification du document dans la r & DT. Toutefois, si vous créez un affichage personnalisé d’un document qui n’utilise pas une fenêtre de document standard \(autrement dit, il n’implémente pas le <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> interface\), vous devez définir votre propre verrou de modification. Par exemple, dans l’Assistant, un document est modifié sans être ouvert dans un éditeur. Pour les verrous de document être ouvert par les Assistants et des entités similaires, ces entités doivent implémenter le <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder> interface. Pour inscrire votre support de verrouillage de documents, appelez le <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.RegisterDocumentLockHolder%2A> \(méthode\) et passez votre <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder> mise en œuvre. Cela ajoute votre support de verrouillage de documents à la r & DT. Un autre scénario d’implémentation d’un support de verrouillage de documents est que si vous ouvrez un document dans une fenêtre d’outils spéciaux. Dans ce cas, vous ne pouvez pas avoir la fenêtre outil fermer le document. Toutefois, en enregistrant en tant que détenteur du verrou un document dans la r & DT, l’IDE peut appeler votre implémentation de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder.CloseDocumentHolder%2A> méthode pour demander une fermeture du document.  
  
## Autres utilisations de la Table de Document en cours d’exécution  
 D’autres entités de l’IDE utilisent le r & DT pour obtenir des informations sur les documents. Par exemple, le Gestionnaire de contrôle de code source utilise la r & DT d’informer le système de recharger un document dans l’éditeur, une fois qu’il obtient la version la plus récente du fichier. Pour ce faire, le Gestionnaire de contrôle de code source recherche les fichiers dans la r & DT pour voir si elles sont ouvertes. Si elles sont alors que le Gestionnaire de contrôle de code source vérifie que la hiérarchie implémente la <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A> méthode. Si le projet n’implémente pas le <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A> \(méthode\), puis sur la source de contrôle vérifie manager pour une implémentation de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.ReloadDocData%2A> méthode sur l’objet de données de document directement.  
  
 L’IDE utilise également le r & DT à resurface \(amener au premier plan\) un document ouvert, si un utilisateur demande à ce document. Pour plus d'informations, consultez [Afficher les fichiers à l'aide de la commande Ouvrir un fichier](../../extensibility/internals/displaying-files-by-using-the-open-file-command.md). Pour déterminer si un fichier est ouvert dans la r & DT, effectuez les opérations suivantes.  
  
-   Requête du moniker de document \(autrement dit, le chemin d’accès complet de documents\) déterminer si l’élément est ouvert.  
  
-   Utilisez l’ID de hiérarchie ou un élément pour demander le système de projet pour le chemin d’accès complet de documents, puis recherchez l’élément dans la r & DT.  
  
## Voir aussi  
 [Utilisation de RDT\_ReadLock](../../extensibility/internals/rdt-readlock-usage.md)   
 [Persistance et la Table de Document en cours d'exécution](../../extensibility/internals/persistence-and-the-running-document-table.md)