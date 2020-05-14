---
title: Élimination des fichiers SAK Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- temporary files
- ~sak files
- source control plug-ins, ~SAK files
ms.assetid: 5277b5fa-073b-4bd1-8ba1-9dc913aa3c50
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0294198bb1560f8df6f17170013f88d4fe11e5cf
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708500"
---
# <a name="elimination-of-sak-files"></a>Élimination des fichiers SAK
Dans l’API 1.2 de contrôle des sources, les fichiers *SAK* ont été remplacés par des indicateurs de capacité et de nouvelles fonctions qui détectent si un plug-in de contrôle source prend en charge le fichier *MSSCCPRJ* et les caisses partagées.

## <a name="sak-files"></a>Fichiers SAK
Visual Studio .NET 2003 a créé des fichiers temporaires préfixés avec *SAK*. Ces fichiers sont utilisés pour déterminer si un plug-in de contrôle source prend en charge :

- Le fichier *MSSCCPRJ.SCC.*

- Caisses multiples (partagées).

Pour les plug-ins qui prennent en charge les fonctions avancées fournies dans l’API 1.2 de contrôle source, l’IDE peut détecter ces capacités sans créer les fichiers temporaires grâce à l’utilisation de nouvelles capacités, drapeaux et fonctions, détaillés dans les sections suivantes.

## <a name="new-capability-flags"></a>Nouveaux drapeaux de capacité
 `SCC_CAP_SCCFILE`

 `SCC_CAP_MULTICHECKOUT`

## <a name="new-functions"></a>Nouvelles fonctions
- [SccWillCreateSccFile](../../extensibility/sccwillcreatesccfile-function.md)

- [SccIsMultiCheckoutEnabled](../../extensibility/sccismulticheckoutenabled-function.md)

 Si un plug-in de contrôle source prend en charge plusieurs `SCC_CAP_MULTICHECKOUT` caisses (partagées), il déclare la capacité et implémente la `SccIsMultiCheckOutEnabled` fonction. Cette fonction est appelée chaque fois qu’une opération de caisse se produit sur l’un des projets contrôlés par la source.

 Si un plug-in de contrôle source prend en charge la création et l’utilisation `SCC_CAP_SCCFILE` d’un fichier *MSSCCPRJ.SCC,* il déclare la capacité et implémente le [SccWillCreateSccFile](../../extensibility/sccwillcreatesccfile-function.md). Cette fonction est appelée avec une liste de fichiers. La fonction `TRUE' or 'FALSE` revient pour chaque fichier pour indiquer si Visual Studio devrait utiliser un fichier *MSSCCPRJ.SCC* pour cela. Si le plug-in de contrôle source choisit de ne pas prendre en charge ces nouvelles capacités et fonctions, il peut utiliser la clé de registre suivante pour désactiver la création de ces fichiers :

 **[HKEY_CURRENT_USER-Software-Microsoft-VisualStudio-8.0-SourceControl] DoNotCreateTemporaryFilesInSourceControl** = *dword:00000001*

> [!NOTE]
> Si cette clé de registre est réglée à *dword:000000000*, il est équivalent à la clé étant inexistante, et Visual Studio tente toujours de créer les fichiers temporaires. Toutefois, si la clé de registre est configuré pour *dword:00000001*, Visual Studio ne tente pas de créer les fichiers temporaires. Au lieu de cela, il suppose que le plug-in de contrôle source ne prend pas en charge le fichier *MSSCCPRJ.SCC* et ne prend pas en charge les caisses partagées.

## <a name="see-also"></a>Voir aussi
- [Nouveauté dans la version API 1.2 du contrôle source](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)
