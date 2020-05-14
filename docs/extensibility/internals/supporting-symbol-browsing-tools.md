---
title: Outils de soutien à la navigation des symboles (en anglais seulement) Microsoft Docs
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
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4998e47ccd6f99df2710833c18975d57e3bb92f5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704765"
---
# <a name="supporting-symbol-browsing-tools"></a>Prise en charge des outils de consultation de symbole
**Le navigateur d’objets**, **la vue de classe,** **le navigateur d’appel** et les outils de **résultats de symbole** fournissent des capacités de navigation de symbole dans Visual Studio. Ces outils affichent des vues hiérarchiques des arbres des symboles et montrent les relations entre les symboles de l’arbre. Les symboles peuvent représenter des espaces de noms, des objets, des classes, des membres de la classe et d’autres éléments linguistiques contenus dans divers composants. Les composants comprennent des projets Visual Studio, des composants cadres .NET externes et des bibliothèques de type (.tlb). Pour plus d’informations, voir [Voir la structure du code](../../ide/viewing-the-structure-of-code.md).

## <a name="symbol-browsing-libraries"></a>Bibliothèques de sourcils
 En tant qu’implémentateur de langue, vous pouvez étendre les capacités de navigation des symboles Visual Studio en créant des bibliothèques qui suivent les symboles de vos composants et fournissent les listes de symboles au gestionnaire d’objets Visual Studio à travers un ensemble d’interfaces. Une bibliothèque est <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2> décrite par l’interface. Le gestionnaire d’objets Visual Studio répond aux demandes de nouvelles données provenant des outils de navigation des symboles en obtenant les données des bibliothèques et en les organisant. Il remplit ou met à jour les outils avec les données demandées. Pour obtenir une référence au gestionnaire <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2>d’objets <xref:Microsoft.VisualStudio.Shell.Interop.SVsObjectManager> Visual Studio, passez l’ID de service à la `GetService` méthode.

 Chaque bibliothèque doit s’inscrire auprès du gestionnaire d’objets Visual Studio, qui recueille les informations sur toutes les bibliothèques. Pour enregistrer une bibliothèque, appelez la <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterSimpleLibrary%2A> méthode. Selon l’outil qui déclenche la demande, le gestionnaire d’objets Visual Studio trouve la bibliothèque appropriée et demande des données. Les données circulent entre les [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] bibliothèques et le gestionnaire <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2> de l’objet dans des listes de symboles décrits par l’interface.

 Le [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] gestionnaire d’objets est responsable des outils de navigation de symboles périodiquement rafraîchissants pour refléter les données les plus récentes contenues dans les bibliothèques.

 Le diagramme ci-dessous contient un échantillon d’éléments clés du processus de demande/échange de données entre une bibliothèque et le gestionnaire d’objets Visual Studio. Les interfaces du diagramme font partie d’une application de code gérée.

 ![Flux de données entre une bibliothèque et le gestionnaire d'objets](../../extensibility/internals/media/callbrowserdiagram.gif "CallBrowserDiagram CallBrowserDiagram CallBrowserDiagram CallBrow")

 Pour fournir les listes de symboles au gestionnaire d’objets Visual Studio, vous <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterSimpleLibrary%2A> devez d’abord enregistrer la bibliothèque auprès du gestionnaire d’objets Visual Studio en appelant la méthode. Une fois la bibliothèque enregistrée, le gestionnaire d’objets Visual Studio demande certaines informations sur les capacités de la bibliothèque. Par exemple, il demande les drapeaux de <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2.GetLibFlags2%2A> la <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2.GetSupportedCategoryFields2%2A> bibliothèque et les catégories de support en appelant les et les méthodes. À un moment donné, lorsque l’un des outils demande des données de cette <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2.GetList2%2A> bibliothèque, le gestionnaire d’objets demande la liste de haut niveau des symboles en appelant la méthode. En réponse, la bibliothèque fabrique une liste de symboles et l’expose au gestionnaire d’objets Visual Studio à travers l’interface. <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2> Le [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] gestionnaire de l’objet détermine le nombre <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetItemCount%2A> d’éléments dans la liste en appelant la méthode. Toutes les demandes suivantes se rapportent à un élément donné dans la liste et fournissent le numéro d’index de l’élément dans chaque demande. Le gestionnaire d’objets Visual Studio procède à la collecte de l’information <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetCategoryField2%2A> sur le type, l’accessibilité et d’autres propriétés de l’article en appelant la méthode.

 Il détermine le nom de l’élément en appelant la <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetTextWithOwnership%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetDisplayData%2A> méthode et demande les informations de l’icône en appelant la méthode. L’icône est affichée à gauche du nom de l’élément et représente le type de l’élément, l’accessibilité et d’autres propriétés.

 Le [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] gestionnaire d’objets appelle la <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetExpandable3%2A> méthode pour déterminer si un élément de liste donné est extensible et a des articles pour enfants. Si l’interface utilisateur envoie une demande d’extension d’un élément, le gestionnaire d’objets demande à l’enfant la liste des symboles en appelant la <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetList2%2A> méthode. Le processus se poursuit avec différentes parties de l’arbre en cours de construction sur demande.

> [!NOTE]
> Pour implémenter un fournisseur <xref:Microsoft.VisualStudio.Shell.Interop.IVsLibrary2> <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectList2> de symboles de code natif, utilisez les interfaces et les interfaces.

## <a name="see-also"></a>Voir aussi
- [Guide pratique pour inscrire une bibliothèque avec le Gestionnaire d’objets](../../extensibility/internals/how-to-register-a-library-with-the-object-manager.md)
- [Guide pratique pour exposer des listes de symboles fournies par la bibliothèque au Gestionnaire d’objets](../../extensibility/internals/how-to-expose-lists-of-symbols-provided-by-the-library-to-the-object-manager.md)
- [Guide pratique pour identifier les symboles dans une bibliothèque](../../extensibility/internals/how-to-identify-symbols-in-a-library.md)
