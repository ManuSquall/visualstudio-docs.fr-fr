---
title: Prise en charge des outils de consultation de symbole | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- symbols, symbol-browsing tools
- browsers, symbol browsers
- symbol-browsing tools
- libraries
- IVsLibrary2 interface, symbol-browsing tools
- IVsSimpleLibrary2 interface, symbol-browsing tools
- symbol-browsing tools, library manager
- symbols
- libraries, symbol-browsing tools
ms.assetid: 70d8c9e5-4b0b-4a69-b3b3-90f36debe880
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 649ba0583a70d0d53d8b12f26573daf3c52cf5e9
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66331203"
---
# <a name="supporting-symbol-browsing-tools"></a>Prise en charge des outils de consultation de symbole
**Explorateur d’objets**, **affichage de classes**, **Explorateur d’appels** et **résultats** outils fournissent des fonctionnalités dans Visual Studio de recherche de symboles. Ces outils affichent des vues de l’arborescence hiérarchique des symboles et les relations entre les symboles dans l’arborescence. Les symboles peuvent représenter des espaces de noms, les objets, les classes, les membres de classe et les autres éléments de langage contenus dans les différents composants. Les composants incluent des projets Visual Studio, externes [!INCLUDE[dnprdnshort](../../code-quality/includes/dnprdnshort_md.md)] composants et bibliothèques de types (.tlb). Pour plus d’informations, consultez [Affichage de la structure du code](../../ide/viewing-the-structure-of-code.md).

## <a name="symbol-browsing-libraries"></a>Bibliothèques de recherche de symboles
 En tant qu’un implémenteur de langage, vous pouvez étendre les fonctionnalités de recherche de symboles Visual Studio en créant des bibliothèques de suivi des symboles dans vos composants et de fournissent les listes de symboles pour le Gestionnaire d’objets de Visual Studio via un ensemble d’interfaces. Une bibliothèque est décrite par la <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2> interface. Le Gestionnaire d’objets de Visual Studio répond aux demandes de nouvelles données à partir des outils de consultation de symboles par l’obtention de données à partir des bibliothèques et d’organisation. Par la suite, il remplit ou met à jour les outils avec les données demandées. Pour obtenir une référence pour le Gestionnaire d’objets de Visual Studio, <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2>, transmettez le <xref:Microsoft.VisualStudio.Shell.Interop.SVsObjectManager> ID de service le `GetService` (méthode).

 Chaque bibliothèque doit inscrire avec le Gestionnaire d’objets de Visual Studio, qui collecte les informations sur toutes les bibliothèques. Pour inscrire une bibliothèque, appelez le <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterSimpleLibrary%2A> (méthode). Selon quel outil initialise la demande, le Gestionnaire d’objets de Visual Studio recherche la bibliothèque appropriée et demande des données. Les données transitent entre les bibliothèques et les [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Gestionnaire d’objets dans les listes de symboles décrits par le <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2> interface.

 Le [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Gestionnaire d’objets est responsable de l’actualiser périodiquement les outils de consultation du symbole pour refléter les données les plus récentes contenues dans les bibliothèques.

 Le diagramme ci-dessous contient un groupe d’éléments clés du processus de requêtes/données exchange entre une bibliothèque et le Gestionnaire d’objets de Visual Studio. Les interfaces dans le diagramme font partie d’une application de code managé.

 ![Flux de données entre une bibliothèque et le Gestionnaire d’objets](../../extensibility/internals/media/callbrowserdiagram.gif "CallBrowserDiagram")

 Pour fournir les listes de symboles pour le Gestionnaire d’objets de Visual Studio, vous devez d’abord inscrire la bibliothèque avec le Gestionnaire d’objets de Visual Studio en appelant le <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterSimpleLibrary%2A> (méthode). Une fois que la bibliothèque est enregistrée, le Gestionnaire d’objets de Visual Studio demande certaines informations sur les fonctionnalités de la bibliothèque. Par exemple, il demande les indicateurs de bibliothèque et prise en charge des catégories en appelant le <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2.GetLibFlags2%2A> et <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2.GetSupportedCategoryFields2%2A> méthodes. À un moment donné, lorsqu’un des outils de demande des données à partir de cette bibliothèque, le Gestionnaire d’objets demande la liste de niveau supérieur de symboles en appelant le <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2.GetList2%2A> (méthode). En réponse, la bibliothèque de fabrique d’une liste de symboles et l’expose pour le Gestionnaire d’objets de Visual Studio via le <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2> interface. Le [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Gestionnaire d’objets détermine le nombre d’éléments figurent dans la liste en appelant le <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetItemCount%2A> (méthode). Toutes les demandes suivantes se rapportent à un élément donné dans la liste et fournissent le numéro d’index élément dans chaque demande. Le Gestionnaire d’objets de Visual Studio se poursuit pour collecter les informations sur le type, l’accessibilité et d’autres propriétés de l’élément en appelant le <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetCategoryField2%2A> (méthode).

 Il détermine le nom de l’élément en appelant le <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetTextWithOwnership%2A> (méthode) et demande les informations de l’icône en appelant le <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetDisplayData%2A> (méthode). L’icône s’affiche à gauche du nom de l’élément et indique le type de l’élément, l’accessibilité et d’autres propriétés.

 Le [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] object manager appelle le <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetExpandable3%2A> méthode pour déterminer si un élément de liste donné peut être développé et a des éléments enfants. Si l’interface utilisateur envoie une demande pour développer un élément, le Gestionnaire d’objets demande la liste des symboles enfants en appelant le <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetList2%2A> (méthode). Le processus se poursuit avec les différentes parties de l’arborescence en cours de génération à la demande.

> [!NOTE]
> Pour implémenter un fournisseur de symboles du code natif, utilisez le <xref:Microsoft.VisualStudio.Shell.Interop.IVsLibrary2> et <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectList2> interfaces.

## <a name="see-also"></a>Voir aussi
- [Guide pratique pour inscrire une bibliothèque avec le Gestionnaire d’objets](../../extensibility/internals/how-to-register-a-library-with-the-object-manager.md)
- [Guide pratique pour exposer des listes de symboles fournies par la bibliothèque au Gestionnaire d’objets](../../extensibility/internals/how-to-expose-lists-of-symbols-provided-by-the-library-to-the-object-manager.md)
- [Guide pratique pour identifier les symboles dans une bibliothèque](../../extensibility/internals/how-to-identify-symbols-in-a-library.md)