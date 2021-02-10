---
title: Cibler des versions antérieures du .NET Framework pour F#
description: Découvrez-en plus sur le ciblage d’une version antérieure du .NET Framework lors de l’utilisation de F# dans Visual Studio.
ms.date: 07/11/2018
ms.topic: troubleshooting
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- dotnet
monikerRange: vs-2017
ms.openlocfilehash: fe9d87a5cdea04251d7ab30b6e9e0fed6b0c4b31
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99945524"
---
# <a name="target-older-versions-of-net-f"></a>Cibler des versions antérieures de .NET (F#)

L’erreur suivante peut apparaître si vous essayez de cibler .NET Framework 2.0, 3.0 ou 3.5 dans un projet F# quand Visual Studio est installé sur Windows 8.1 :

**Ce projet nécessite le runtime F# 2.0, mais ce runtime n’est pas installé.**

Cette erreur se produit lorsque les conditions suivantes sont réunies :

- Vous avez installé Visual Studio sur Windows 8.1.

- Vous n’avez pas activé .NET Framework 3.5 avant d’installer Visual Studio.

- Votre projet cible .NET Framework 2.0, 3.0 ou 3.5.

Quand vous installez Visual Studio, celui-ci détecte les versions installées du .NET Framework. Visual Studio installe le runtime F# 2.0 uniquement si .NET Framework 3.5 est installé et activé.

## <a name="resolve-the-error"></a>Résoudre l’erreur

Pour résoudre cette erreur, vous pouvez :

- Cibler une version plus récente du .NET Framework, ou

- Activer .NET Framework 3.5 sur Windows 8.1, puis installer le runtime F# 2.0 en réparant l’installation de Visual Studio. Les étapes à effectuer sont décrites ci-dessous.

### <a name="to-enable-the-net-framework-35-on-windows-81"></a>Pour activer .NET Framework 3.5 sur Windows 8.1

1. Dans l’écran **Démarrer**, tapez **Panneau de configuration**.

   Lors de la frappe, l’icône **Panneau de configuration** s’affiche sous le titre **Applications**.

2. Choisissez l’icône **Panneau de configuration**, l’icône **Programmes**, puis le lien **Activer ou désactiver des fonctionnalités Windows**.

3. Vérifiez que la case **.NET Framework 3.5 (inclut .NET 2.0 et 3.0)** est cochée, puis choisissez le bouton **OK**. Vous n’avez pas besoin de cocher des cases pour les nœuds enfants des composants facultatifs du .NET Framework.

   .NET Framework 3.5 est activé s’il ne l’était pas.

### <a name="to-install-the-f-20-runtime"></a>Pour installer le runtime F# 2.0

Suivez les [étapes de réparation de Visual Studio](../install/repair-visual-studio.md).

## <a name="see-also"></a>Voir aussi

- [Guide F# (.NET Framework)](/dotnet/fsharp/)
- [F# dans Visual Studio](fsharp-visual-studio.md)
