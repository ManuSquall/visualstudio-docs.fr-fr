---
title: Nouveautés de MSBuild 16.0 | Microsoft Docs
ms.date: 03/11/2019
ms.topic: conceptual
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
monikerRange: '>=vs-2019'
ms.openlocfilehash: abd8ba039f9f6a19f5c028e05c03151c090e304c
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77631001"
---
# <a name="whats-new-in-msbuild-160"></a>Nouveautés de MSBuild 16.0

Cet article décrit les fonctionnalités et propriétés mises à jour dans MSBuild 16.0. Pour obtenir des notes de publication détaillées, consultez [MSBuild 16,0](https://github.com/microsoft/msbuild/releases/tag/v16.0.461.62831).

## <a name="changed-path"></a>Chemin d’accès modifié

 MSBuild est installé dans le dossier *\Current* sous chaque version de Visual Studio. Par exemple, *C:\Program Files (x86)\Microsoft Visual Studio\Current\Enterprise\MSBuild*. Vous pouvez également localiser MSBuild à l’aide du module PowerShell suivant : [vssetup.powershell](https://github.com/Microsoft/vssetup.powershell).

## <a name="changed-properties"></a>Propriétés modifiées

 Les propriétés MSBuild ci-après ont été mises à jour afin de correspondre au nouveau numéro de version.

- `MSBuildToolsVersion` pour cette version des outils présente la valeur « Current ». La version d’assembly est la même que dans Visual Studio 2017, à savoir 15.1.0.0.

- `VisualStudioVersion` pour cette version des outils présente la valeur « 16.0 »

## <a name="updates"></a>Mises à jour

MSBuild et Visual Studio ciblent maintenant .NET Framework 4.7.2. Si vous souhaitez utiliser de nouvelles fonctionnalités de l’API MSBuild, vous devez également mettre à niveau votre assembly, mais le code existant continuera de fonctionner.

## <a name="see-also"></a>Voir aussi

- [MSBuild](../msbuild/msbuild.md)
