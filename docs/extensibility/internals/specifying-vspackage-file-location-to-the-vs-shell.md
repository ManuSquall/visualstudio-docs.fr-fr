---
title: Spécification de l’emplacement du fichier VSPackage dans le shell VS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- managed VSPackages, file location
- VSPackages, managed package file location
ms.assetid: beb8607a-4183-4ed2-9ac8-7527f11513b1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f112da4e79bff06d12472f0af7a3fe47b2f25da4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80704979"
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
