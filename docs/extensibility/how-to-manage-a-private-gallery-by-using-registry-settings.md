---
title: Gérer une galerie privée à l’aide des paramètres du Registre
description: Découvrez comment contrôler l’accès aux contrôles, aux modèles et aux outils de la Galerie Visual Studio, de la Galerie d’exemples ou de galeries privées.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- VSIX private galleries, managing
- managing VSIX private galleries
ms.assetid: 86b86442-4293-4cad-9fe2-876eef65f426
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 9fef1e6447ac07e9c3d4ccfb76a9ee1e06f91e42
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112898833"
---
# <a name="how-to-manage-a-private-gallery-by-using-registry-settings"></a>Procédure : gérer une galerie privée à l’aide des paramètres du Registre
Si vous êtes administrateur ou développeur d’une extension de Shell isolé, vous pouvez contrôler l’accès aux contrôles, aux modèles et aux outils de la Galerie Visual Studio, de la Galerie d’exemples ou de galeries privées. Pour rendre une galerie disponible ou non, créez un fichier *. pkgdef* qui décrit les clés de Registre modifiées et leurs valeurs.

## <a name="manage-private-galleries"></a>Gérer les galeries privées
 Vous pouvez créer un fichier *. pkgdef* pour contrôler l’accès aux galeries sur plusieurs ordinateurs. Ce fichier doit avoir le format suivant.

```
[$RootKey$\ExtensionManager\Repositories\{UniqueGUID}]
@={URI}  (REG_SZ)
Disabled=0 | 1 (DWORD)
Priority=0 (highest priority) ... MaxInt (lowest priority) (DWORD) (uint)
Protocol=Atom Feed|Sharepoint (REG_SZ)
DisplayName={DisplayName} (REG_SZ)
DisplayNameResourceID={ID} (REG_SZ)
DisplayNamePackageGuid={GUID} (REG_SZ)

```

 La `Repositories` clé fait référence à la galerie à activer ou à désactiver. La Galerie Visual Studio et la Galerie d’exemples utilisent les GUID de référentiel suivants :

- Galerie Visual Studio : 0F45E408-7995-4375-9485-86B8DB553DC9

- Galerie d’exemples : AEB9CB40-D8E6-4615-B52C-27E307F8506C

  La `Disabled` valeur est facultative. Par défaut, une galerie est activée.

  La `Priority` valeur détermine l’ordre dans lequel les galeries sont répertoriées dans la boîte de dialogue **options** . La Galerie Visual Studio a la priorité 10 et la Galerie d’exemples a la priorité 20. Les galeries privées commencent à la priorité 100. Si plusieurs galeries ont la même valeur de priorité, l’ordre dans lequel elles apparaissent est déterminé par les valeurs de leurs attributs localisés `DisplayName` .

  La `Protocol` valeur est requise pour les galeries basées sur Atom ou sur SharePoint.

  `DisplayName`Ou bien, `DisplayNameResourceID` et `DisplayNamePackageGuid` doivent être spécifiés. Si tous les sont spécifiés, `DisplayNameResourceID` la `DisplayNamePackageGuid` paire et est utilisée.

## <a name="disable-the-visual-studio-gallery-using-a-pkgdef-file"></a>Désactiver la Galerie Visual Studio à l’aide d’un fichier. pkgdef
 Vous pouvez désactiver une galerie dans un fichier *. pkgdef* . L’entrée suivante désactive la Galerie Visual Studio :

```
[$RootKey$\ExtensionManager\Repositories\{0F45E408-7995-4375-9485-86B8DB553DC9}]
"Disabled"=dword:00000001

```

 L’entrée suivante désactive la Galerie d’exemples :

```
[$RootKey$\ExtensionManager\Repositories\{AEB9CB40-D8E6-4615-B52C-27E307F8506C}]
"Disabled"=dword:00000001

```

## <a name="see-also"></a>Voir aussi
- [Galeries privées](../extensibility/private-galleries.md)
