---
title: 'Comment : Gérer une galerie privée en utilisant les paramètres du registre . Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSIX private galleries, managing
- managing VSIX private galleries
ms.assetid: 86b86442-4293-4cad-9fe2-876eef65f426
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a2630fc71bea40a4d05e616ae336759ba62431a0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710930"
---
# <a name="how-to-manage-a-private-gallery-by-using-registry-settings"></a>Comment : Gérer une galerie privée en utilisant les paramètres du registre
Si vous êtes administrateur ou développeur d’une extension De shell isolée, vous pouvez contrôler l’accès aux commandes, aux modèles et aux outils de la Visual Studio Gallery, de la Samples Gallery ou de galeries privées. Pour rendre une galerie disponible ou indisponible, créez un fichier *.pkgdef* qui décrit les clés de registre modifiées et leurs valeurs.

## <a name="manage-private-galleries"></a>Gérer les galeries privées
 Vous pouvez créer un fichier *.pkgdef* pour contrôler l’accès aux galeries sur plusieurs ordinateurs. Ce fichier doit avoir le format suivant.

```
[$RootKey$\ExtensionManager\Repositories\{UniqueGUID}]
@={URI}  (REG_SZ)
Disabled=0 | 1 (DWORD)
Priority=0 (highest priority) ... MaxInt (lowest priority) (DWORD) (uint)
Protocol=Atom Feed|Sharepoint (REG_SZ)
DisplayName={DisplayName} (REG_SZ)
DisplayNameResourceID={ID} (REG_SZ)
DisplayNamePackageGuid={GUID} (REG_SZ)

```

 La `Repositories` clé se réfère à la galerie pour être activé ou désactivé. La Visual Studio Gallery et la Samples Gallery utilisent les GUIDs de dépôt suivants :

- Galerie Visual Studio : 0F45E408-7995-4375-9485-86B8DB553DC9

- Galerie d’échantillons : AEB9CB40-D8E6-4615-B52C-27E307F8506C

  La `Disabled` valeur est facultative. Par défaut, une galerie est activée.

  La `Priority` valeur détermine l’ordre dans lequel les galeries sont répertoriées dans la boîte de dialogue **Options.** Visual Studio Gallery a la priorité 10 et la Galerie Des échantillons a la priorité 20. Les galeries privées commencent à la priorité 100. Si plusieurs galeries ont la même valeur prioritaire, l’ordre dans lequel `DisplayName` elles apparaissent est déterminé par les valeurs de leurs attributs localisés.

  La `Protocol` valeur est requise pour les galeries basées sur Atom ou SharePoint.

  Soit, `DisplayName`ou `DisplayNameResourceID` `DisplayNamePackageGuid`les deux et , doit être spécifié. Si tous sont spécifiés, alors la `DisplayNameResourceID` paire et `DisplayNamePackageGuid` la paire est utilisée.

## <a name="disable-the-visual-studio-gallery-using-a-pkgdef-file"></a>Désactiver la Visual Studio Gallery à l’aide d’un fichier .pkgdef
 Vous pouvez désactiver une galerie dans un fichier *.pkgdef.* L’entrée suivante désactive la Visual Studio Gallery :

```
[$RootKey$\ExtensionManager\Repositories\{0F45E408-7995-4375-9485-86B8DB553DC9}]
"Disabled"=dword:00000001

```

 L’entrée suivante désactive la Galerie des échantillons :

```
[$RootKey$\ExtensionManager\Repositories\{AEB9CB40-D8E6-4615-B52C-27E307F8506C}]
"Disabled"=dword:00000001

```

## <a name="see-also"></a>Voir aussi
- [Galeries privées](../extensibility/private-galleries.md)
