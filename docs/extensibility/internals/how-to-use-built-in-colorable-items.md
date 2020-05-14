---
title: 'Comment: Utilisez des articles colorables intégrés Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- colorable items
- language services, built-in colorable items
ms.assetid: 5e5f3436-6bad-4fd2-8823-6a30353ba648
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 34e07894c3306f544396e53001990f7b9a2df5a0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707786"
---
# <a name="how-to-use-built-in-colorable-items"></a>Comment: Utilisez des articles colorables intégrés
Avant d’utiliser les éléments colorables intégrés, vous devez d’abord signaler à l’environnement de développement intégré (IDE) que vous ne fournissez pas vos propres éléments colorables personnalisés, qui dans ce cas seraient <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems> des objets. Pour ce faire, vous fixez une inscription au registre pour le service linguistique.

## <a name="to-use-built-in-colorable-items"></a>Utiliser des articles colorables intégrés

1. Sous **HKEY_LOCAL_MACHINE-VisualStudio\\<X.Y>-Langues-Services linguistiques\\<Nom\>de langue**, où \<X.Y> est [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] une \<version et le nom de langue> est le nom de votre langue, créez une valeur d’entrée de registre DWORD appelée **RequestStockColors**.

2. Définissez la valeur d’entrée du registre **RequestStockColors** à *1*.

    Après avoir créé l’entrée du <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> registre, la méthode <xref:Microsoft.VisualStudio.TextManager.Interop.DEFAULTITEMS> de votre colorateur peut utiliser les membres de l’énumération pour remplir la gamme d’attributs de couleur pour une utilisation par l’éditeur.

   > [!NOTE]
   > Ne définissez pas cette entrée de registre si vous fournissez des articles colorables personnalisés. Pour plus d’informations, voir [articles colorables personnalisés](../../extensibility/internals/custom-colorable-items.md).

## <a name="see-also"></a>Voir aussi
- [Coloriage Syntax dans les éditeurs personnalisés](../../extensibility/syntax-coloring-in-custom-editors.md)
- [Coloriage Syntax dans un service linguistique hérité](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)
- [Mise en œuvre de la coloration syntaxe](../../extensibility/internals/implementing-syntax-coloring.md)
- [Articles colorables personnalisés](../../extensibility/internals/custom-colorable-items.md)
- [Enregistrer un service linguistique hérité](../../extensibility/internals/registering-a-legacy-language-service2.md)
