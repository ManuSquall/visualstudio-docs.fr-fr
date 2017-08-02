---
title: "Prise en charge d&#39;outils de consultation du symbole | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "symboles, outils de consultation du symbole"
  - "navigateurs, les navigateurs de symbole"
  - "outils de consultation du symbole"
  - "bibliothèques"
  - "Interface IVsLibrary2, outils de consultation du symbole"
  - "Interface IVsSimpleLibrary2, outils de consultation du symbole"
  - "outils de consultation du symbole, le Gestionnaire de bibliothèque"
  - "symboles"
  - "bibliothèques, outils de consultation du symbole"
ms.assetid: 70d8c9e5-4b0b-4a69-b3b3-90f36debe880
caps.latest.revision: 26
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 26
---
# Prise en charge d&#39;outils de consultation du symbole
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Les outils d'**Explorateur d'objets**, d' **Affichage de classes**, d' **Explorateur d'appels** et de **Résultats de la recherche de symbole** fournissent des fonctionnalités de navigation de symbole dans Visual Studio.  Ces outils affichent des arborescences hiérarchiques des symboles et affichent les relations entre les symboles dans l'arborescence.  Les symboles peuvent représenter des espaces de noms, des objets, des classes, des membres de la classe, et d'autres éléments de langage contenus dans différents composants.  Les composants incluent les projets Visual Studio, les composants externes de [!INCLUDE[dnprdnshort](../../code-quality/includes/dnprdnshort_md.md)] et des bibliothèques de types \(.tlb\).  Pour plus d'informations, consultez [Affichage de la structure du code](../../ide/viewing-the-structure-of-code.md).  
  
## bibliothèques de Symbole\-Navigation  
 En tant qu'implémenteur de langage, vous pouvez étendre les fonctions de symbole\-navigation Visual Studio en créant des bibliothèques qui suivent les symboles dans les composants et fournissent des listes de symboles dans le gestionnaire d'objets de Visual Studio via un jeu d'interfaces.  Une bibliothèque est représentée par l'interface d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2> .  Le gestionnaire d'objets Visual Studio répond aux demandes de nouvelles données des outils de symbole\-navigation en obtenant les données des bibliothèques et en les organisant.  Il ensuite remplit ou met à jour outils avec les données demandées.  Pour obtenir une référence au gestionnaire d'objets de Visual Studio, <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2>, passez l'ID de service d' <xref:Microsoft.VisualStudio.Shell.Interop.SVsObjectManager> à la méthode d' `GetService` .  
  
 Chaque bibliothèque doit s'inscrire le gestionnaire d'objets Visual Studio, qui collecte les informations sur toutes les bibliothèques.  Pour inscrire une bibliothèque, appelez la méthode d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterSimpleLibrary%2A> .  Selon l'outil initialise la demande, le gestionnaire d'objets Visual Studio recherche la bibliothèque appropriée et demande de données.  L'itinéraire de données entre les bibliothèques et le gestionnaire d'objets de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]dans les listes de symboles décrits par <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2> interface.  
  
 Le gestionnaire d'objets de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]est chargé d'actualiser régulièrement des outils de symbole\-navigation pour refléter les données les plus récentes contenues dans les bibliothèques.  
  
 Le diagramme ci\-dessous contient un exemple des éléments clés des requêtes par le processus d'échange de données entre une bibliothèque et le gestionnaire d'objets de Visual Studio.  les interfaces dans le diagramme font partie d'une application de code managé.  
  
 ![Flux de données entre une bibliothèque et le gestionnaire d'objets](~/extensibility/internals/media/callbrowserdiagram.gif "CallBrowserDiagram")  
  
 Pour fournir les listes de symboles dans le gestionnaire d'objets de Visual Studio, vous devez d'abord enregistrer la bibliothèque avec le gestionnaire d'objets Visual Studio en appelant la méthode d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterSimpleLibrary%2A> .  Une fois la bibliothèque peut être enregistrée, le gestionnaire d'objets Visual Studio demande certaines informations sur les fonctions de la bibliothèque.  Par exemple, il demande des balises de bibliothèque et les catégories prend en charge en appelant les méthodes d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2.GetLibFlags2%2A> et d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2.GetSupportedCategoryFields2%2A> .  À un moment donné, lorsque l'un des outils demande de données de cette bibliothèque, le gestionnaire d'objets demande la liste de niveau supérieur de symboles en appelant la méthode d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2.GetList2%2A> .  En réponse, la bibliothèque fabrique une liste de symboles et l'expose au gestionnaire d'objets de Visual Studio via l'interface d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2> .  Le gestionnaire d'objets de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]détermine le nombre d'éléments sont dans la liste en appelant la méthode d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetItemCount%2A> .  Toutes les demandes suivantes mettent en relation avec un élément donné dans la liste et fournissent l'index d'élément dans chaque demande.  Le gestionnaire d'objets Visual Studio continue à collecter des informations sur le type, l'accessibilité, et d'autres propriétés de l'élément en appelant la méthode d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetCategoryField2%2A> .  
  
 Il détermine le nom de l'élément en appelant la méthode d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetTextWithOwnership%2A> et demander des informations d'icône en appelant la méthode d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetDisplayData%2A> .  L'icône est affichée à gauche du nom de l'élément et représente le type de l'élément, de l'accessibilité, et d'autres propriétés.  
  
 Le gestionnaire d'objets de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] appelle la méthode d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetExpandable3%2A> pour déterminer si un élément de liste donné peut être développé et a des éléments enfants.  Si l'interface utilisateur envoie une requête de développer un élément, le gestionnaire d'objets demande la liste enfant de symboles en appelant la méthode d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetList2%2A> .  Le processus se poursuit différentes parties de l'arborescence en cours de génération à la demande.  
  
> [!NOTE]
>  Pour implémenter un fournisseur de symbole de code natif, utilisez les interfaces d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsLibrary2> et d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectList2> .  
  
## Voir aussi  
 [Comment : inscrire une bibliothèque avec le Gestionnaire d'objets](../../extensibility/internals/how-to-register-a-library-with-the-object-manager.md)   
 [Comment : exposer de listes de symboles fournis par la bibliothèque pour le Gestionnaire d'objets](../../extensibility/internals/how-to-expose-lists-of-symbols-provided-by-the-library-to-the-object-manager.md)   
 [Comment : identifier les symboles dans une bibliothèque](../../extensibility/internals/how-to-identify-symbols-in-a-library.md)