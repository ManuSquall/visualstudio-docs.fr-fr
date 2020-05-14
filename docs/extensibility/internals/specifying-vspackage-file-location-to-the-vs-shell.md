---
title: Spécifier l’emplacement du fichier VSPackage à la coque VS (fr) Microsoft Docs
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704979"
---
# <a name="specifying-vspackage-file-location-to-the-vs-shell"></a>Spécification de l’emplacement du fichier VSPackage au shell Visual Studio
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]doit être en mesure de localiser le DLL d’assemblage pour charger le VSPackage. Vous pouvez le localiser de diverses façons, comme décrit dans le tableau suivant.

| Méthode | Description |
| - | - |
| Utilisez la clé de registre CodeBase. | La clé CodeBase peut [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] être utilisée pour charger l’assemblage VSPackage à partir de n’importe quelle trajectoire de fichier entièrement qualifiée. La valeur de la clé doit être le chemin de fichier vers le DLL. C’est la meilleure [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] façon d’avoir charger votre assemblage de paquets. Cette technique est parfois appelée la « technique d’annuaire d’installation privée de CodeBase». Lors de l’inscription, la valeur de la base de <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.RegistrationContext> code est transmise aux classes d’attribut d’enregistrement par une instance du type. |
| Placez le DLL dans le répertoire **PrivateAssemblies.** | Placez l’assemblée dans la sous-direction [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] privée des **Assemblées** du répertoire. Les assemblages situés dans **PrivateAssemblies** sont automatiquement détectés, mais ne sont pas visibles dans la boîte de dialogue **Add References.** La différence entre **PrivateAssemblies** et **PublicAssemblies** est que les assemblées dans **PublicAssemblies** sont énumérées dans la boîte de dialogue **Add References.** Si vous avez choisi de ne pas utiliser la technique "CodeBase/annuaire d’installation privée", alors vous devez installer dans le répertoire **PrivateAssemblies.** |
| Utilisez une assemblée forte et la clé du registre de l’Assemblée. | La clé d’assemblage peut [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] être utilisée pour diriger explicitement une forte assemblage VSPackage. La valeur de la clé doit être le nom fort de l’assemblée. |
| Placez le DLL dans le répertoire **PublicAssemblies.** | Enfin, l’assemblage peut également être placé dans la sous-direction **de PublicAssemblies.** Les assemblages situés dans **PublicAssemblies** sont automatiquement détectés, et apparaîtront également dans la boîte de dialogue **Add References** dans [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].<br /><br /> Les assemblages VSPackage ne doivent être placés dans **l’annuaire PublicAssemblies que s’ils** contiennent des composants gérés qui sont destinés à être réutilisés par d’autres développeurs VSPackage. La majorité des assemblées ne répondent pas à ce critère. |

> [!NOTE]
> Utilisez des assemblages signés et nommés pour tous vos assemblées dépendantes. Ces assemblages doivent également être installés dans votre propre répertoire ou le cache d’assemblage global (GAC). Cela protège contre les conflits avec les assemblées qui ont le même nom de fichier de base, connu sous le nom de liaison de nom faible.
