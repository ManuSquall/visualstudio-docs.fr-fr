---
title: Prise en charge des outils de navigation de symboles | Microsoft Docs
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
ms.openlocfilehash: ca171fa75adda3deef5b941852fc3e6c648c84c6
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72723082"
---
# <a name="supporting-symbol-browsing-tools"></a>Prise en charge des outils de consultation de symbole
Les outils **Explorateur d’objets**, **affichage de classes**, **Explorateur d’appels** et rechercher les **résultats de symboles** fournissent des fonctionnalités de navigation de symboles dans Visual Studio. Ces outils affichent des arborescences hiérarchiques de symboles et affichent les relations entre les symboles dans l’arborescence. Les symboles peuvent représenter des espaces de noms, des objets, des classes, des membres de classe et d’autres éléments de langage contenus dans différents composants. Les composants incluent les projets Visual Studio, les composants .NET Framework externes et les bibliothèques de types (. tlb). Pour plus d’informations, consultez [Affichage de la structure du code](../../ide/viewing-the-structure-of-code.md).

## <a name="symbol-browsing-libraries"></a>Bibliothèques de navigation de symboles
 En tant qu’implémenteur de langage, vous pouvez étendre les fonctionnalités de navigation de symboles de Visual Studio en créant des bibliothèques qui effectuent le suivi des symboles dans vos composants et fournissent les listes de symboles au gestionnaire d’objets de Visual Studio via un ensemble d’interfaces. Une bibliothèque est décrite par l’interface <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2>. Le gestionnaire d’objets Visual Studio répond aux demandes de nouvelles données à partir des outils de navigation de symboles en obtenant les données des bibliothèques et en les organisant. Par la suite, il remplit ou met à jour les outils avec les données demandées. Pour obtenir une référence au gestionnaire d’objets Visual Studio, <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2>, transmettez l’ID de service <xref:Microsoft.VisualStudio.Shell.Interop.SVsObjectManager> à la méthode `GetService`.

 Chaque bibliothèque doit s’inscrire auprès du gestionnaire d’objets Visual Studio, qui collecte les informations sur toutes les bibliothèques. Pour inscrire une bibliothèque, appelez la méthode <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterSimpleLibrary%2A>. En fonction de l’outil qui lance la demande, le gestionnaire d’objets Visual Studio recherche la bibliothèque appropriée et demande les données. Les données transitent entre les bibliothèques et le gestionnaire d’objets [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] dans les listes de symboles décrits par l’interface <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2>.

 Le gestionnaire d’objets [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] est chargé d’actualiser périodiquement les outils de navigation de symboles pour refléter les données les plus récentes contenues dans les bibliothèques.

 Le diagramme ci-dessous contient un exemple d’éléments clés du processus de demande/échange de données entre une bibliothèque et le gestionnaire d’objets de Visual Studio. Les interfaces du diagramme font partie d’une application de code managé.

 ![Transmission de données entre une bibliothèque et le gestionnaire d’objets](../../extensibility/internals/media/callbrowserdiagram.gif "CallBrowserDiagram")

 Pour fournir les listes de symboles au gestionnaire d’objets de Visual Studio, vous devez d’abord inscrire la bibliothèque auprès du gestionnaire d’objets Visual Studio en appelant la méthode <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterSimpleLibrary%2A>. Une fois la bibliothèque inscrite, le gestionnaire d’objets Visual Studio demande certaines informations sur les fonctionnalités de la bibliothèque. Par exemple, il demande les indicateurs de bibliothèque et les catégories prises en charge en appelant les méthodes <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2.GetLibFlags2%2A> et <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2.GetSupportedCategoryFields2%2A>. À un moment donné, lorsque l’un des outils demande des données de cette bibliothèque, le gestionnaire d’objets demande la liste de symboles de niveau supérieur en appelant la méthode <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2.GetList2%2A>. En réponse, la bibliothèque fabrique une liste de symboles et l’expose au gestionnaire d’objets Visual Studio par le biais de l’interface <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2>. Le gestionnaire d’objets [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] détermine le nombre d’éléments figurant dans la liste en appelant la méthode <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetItemCount%2A>. Toutes les demandes suivantes sont liées à un élément donné dans la liste et fournissent le numéro d’index de l’élément dans chaque demande. Le gestionnaire d’objets de Visual Studio poursuit la collecte des informations sur le type, l’accessibilité et d’autres propriétés de l’élément en appelant la méthode <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetCategoryField2%2A>.

 Elle détermine le nom de l’élément en appelant la méthode <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetTextWithOwnership%2A> et demande les informations sur l’icône en appelant la méthode <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetDisplayData%2A>. L’icône s’affiche à gauche du nom de l’élément et représente le type de l’élément, l’accessibilité et d’autres propriétés.

 Le gestionnaire d’objets [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] appelle la méthode <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetExpandable3%2A> pour déterminer si un élément de liste donné peut être développé et a des éléments enfants. Si l’interface utilisateur envoie une demande pour développer un élément, le gestionnaire d’objets demande la liste enfant de symboles en appelant la méthode <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetList2%2A>. Le processus se poursuit avec différentes parties de l’arborescence qui sont générées à la demande.

> [!NOTE]
> Pour implémenter un fournisseur de symboles de code natif, utilisez les interfaces <xref:Microsoft.VisualStudio.Shell.Interop.IVsLibrary2> et <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectList2>.

## <a name="see-also"></a>Voir aussi
- [Guide pratique pour inscrire une bibliothèque avec le Gestionnaire d’objets](../../extensibility/internals/how-to-register-a-library-with-the-object-manager.md)
- [Guide pratique pour exposer des listes de symboles fournies par la bibliothèque au Gestionnaire d’objets](../../extensibility/internals/how-to-expose-lists-of-symbols-provided-by-the-library-to-the-object-manager.md)
- [Guide pratique pour identifier les symboles dans une bibliothèque](../../extensibility/internals/how-to-identify-symbols-in-a-library.md)