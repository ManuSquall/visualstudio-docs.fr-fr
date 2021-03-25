---
title: Spécification de l’emplacement du fichier VSPackage dans le shell VS | Microsoft Docs
description: Découvrez comment vous pouvez permettre à Visual Studio de localiser la DLL d’assembly pour charger le VSPackage.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- managed VSPackages, file location
- VSPackages, managed package file location
ms.assetid: beb8607a-4183-4ed2-9ac8-7527f11513b1
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: efec1ac3f7ccb3884265f3740108aaef261e9378
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105064067"
---
# <a name="specifying-vspackage-file-location-to-the-vs-shell"></a>Spécification de l’emplacement du fichier VSPackage au shell Visual Studio
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] doit être en mesure de localiser la DLL d’assembly pour charger le VSPackage. Vous pouvez le localiser de différentes manières, comme décrit dans le tableau suivant.

| Méthode | Description |
| - | - |
| Utilisez la clé de Registre code base. | La clé de code base peut être utilisée pour diriger [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] le chargement de l’assembly VSPackage à partir de n’importe quel chemin d’accès de fichier complet. La valeur de la clé doit être le chemin d’accès au fichier DLL. Il s’agit de la meilleure façon de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] charger votre assembly de package. Cette technique est parfois appelée « technique du répertoire d’installation code base/privé ». Pendant l’inscription, la valeur de la base de code est passée aux classes d’attributs d’inscription par le biais d’une instance du <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.RegistrationContext> type. |
| Placez la DLL dans le répertoire **PrivateAssemblies** . | Placez l’assembly dans le sous-répertoire **PrivateAssemblies** du [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] répertoire. Les assemblys situés dans **PrivateAssemblies** sont détectés automatiquement, mais ne sont pas visibles dans la boîte de dialogue **Ajouter des références** . La différence entre **PrivateAssemblies** et **PublicAssemblies** est que les assemblys dans **PublicAssemblies** sont énumérés dans la boîte de dialogue **Ajouter des références** . Si vous avez choisi de ne pas utiliser la technique « répertoire d’installation code base/privé », vous devez installer dans le répertoire **PrivateAssemblies** . |
| Utilisez un assembly avec nom fort et la clé de registre de l’assembly. | La clé d’assembly peut être utilisée pour diriger explicitement le [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] chargement d’un assembly VSPackage nommé fort. La valeur de la clé doit être le nom fort de l’assembly. |
| Placez la DLL dans le répertoire **PublicAssemblies** . | Enfin, l’assembly peut également être placé dans le sous-répertoire **PublicAssemblies** . Les assemblys situés dans **PublicAssemblies** sont automatiquement détectés et s’affichent également dans la boîte de dialogue **Ajouter des références** dans [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .<br /><br /> Les assemblys VSPackage doivent être placés uniquement dans le répertoire **PublicAssemblies** s’ils contiennent des composants gérés qui sont destinés à être réutilisés par d’autres développeurs VSPackage. La majorité des assemblys ne répondent pas à ce critère. |

> [!NOTE]
> Utilisez des assemblys signés avec un nom fort pour tous vos assemblys dépendants. Ces assemblys doivent également être installés dans votre propre répertoire ou dans le Global Assembly Cache (GAC). Cela protège contre les conflits avec les assemblys qui ont le même nom de fichier de base, appelé liaison de nom faible.
