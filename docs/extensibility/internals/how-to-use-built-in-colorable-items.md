---
title: 'Comment : utiliser des éléments coloriables intégrés | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- colorable items
- language services, built-in colorable items
ms.assetid: 5e5f3436-6bad-4fd2-8823-6a30353ba648
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 762d1e53f7aafa11ed345859e68fc98766eec77d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85905221"
---
# <a name="how-to-use-built-in-colorable-items"></a>Comment : utiliser des éléments coloriables intégrés
Avant d’utiliser les éléments coloriables intégrés, vous devez d’abord signaler à l’environnement de développement intégré (IDE) que vous ne fournissez pas vos propres éléments coloriables personnalisés, qui, dans ce cas, sont des <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems> objets. Pour ce faire, vous devez définir une entrée de Registre pour le service de langage.

## <a name="to-use-built-in-colorable-items"></a>Pour utiliser des éléments coloriables intégrés

1. Sous **HKEY_LOCAL_MACHINE \visualstudio \\<X. Y> \languages\language services \\<Language name \> **, où \<X.Y> est une version de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] et \<Language Name> est le nom de votre langue, créez une valeur d’entrée de Registre DWORD appelée **RequestStockColors**.

2. Définissez la valeur de l’entrée de Registre **RequestStockColors** sur *1*.

    Après avoir créé l’entrée de Registre, la méthode de votre Coloriseur <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> peut utiliser les membres de l' <xref:Microsoft.VisualStudio.TextManager.Interop.DEFAULTITEMS> énumération pour remplir le tableau d’attributs de couleur en vue de son utilisation par l’éditeur.

   > [!NOTE]
   > Ne définissez pas cette entrée de Registre si vous fournissez des éléments coloriables personnalisés. Pour plus d’informations, consultez [éléments coloriables personnalisés](../../extensibility/internals/custom-colorable-items.md).

## <a name="see-also"></a>Voir aussi
- [Coloration de la syntaxe dans les éditeurs personnalisés](../../extensibility/syntax-coloring-in-custom-editors.md)
- [Coloration de la syntaxe dans un service de langage hérité](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)
- [Implémentation de la coloration de la syntaxe](../../extensibility/internals/implementing-syntax-coloring.md)
- [Éléments coloriables personnalisés](../../extensibility/internals/custom-colorable-items.md)
- [Inscrire un service de langage hérité](../../extensibility/internals/registering-a-legacy-language-service2.md)
