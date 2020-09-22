---
title: Élimination des fichiers ~ SAK | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- temporary files
- ~sak files
- source control plug-ins, ~SAK files
ms.assetid: 5277b5fa-073b-4bd1-8ba1-9dc913aa3c50
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 751acf4e5f56b7b477f05ab71571e0becd566649
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90839441"
---
# <a name="elimination-of-sak-files"></a>Élimination des fichiers ~SAK
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Dans l’API de plug-in de contrôle de code source 1,2, les fichiers ~ SAK ont été remplacés par des indicateurs de fonctionnalité et de nouvelles fonctions qui détectent si un plug-in de contrôle de code source prend en charge le fichier MSSCCPRJ et les extractions partagées.  
  
## <a name="sak-files"></a>Fichiers ~ SAK  
 Visual Studio .NET 2003 a créé des fichiers temporaires précédés de ~ SAK. Ces fichiers sont utilisés pour déterminer si un plug-in de contrôle de code source prend en charge :  
  
- MSSCCPRJ. Fichier SCC.  
  
- Extractions multiples (partagées).  
  
  Pour les plug-ins qui prennent en charge les fonctions avancées fournies dans l’API de plug-in de contrôle de code source 1,2, l’IDE peut détecter ces fonctionnalités sans créer les fichiers temporaires à l’aide de nouvelles fonctionnalités, de nouveaux indicateurs et de nouvelles fonctions, détaillés dans les sections suivantes.  
  
## <a name="new-capability-flags"></a>Nouveaux indicateurs de capacité  
 `SCC_CAP_SCCFILE`  
  
 `SCC_CAP_MULTICHECKOUT`  
  
## <a name="new-functions"></a>Nouvelles fonctions  
 [SccWillCreateSccFile](../../extensibility/sccwillcreatesccfile-function.md)  
  
 [SccIsMultiCheckoutEnabled](../../extensibility/sccismulticheckoutenabled-function.md)  
  
 Si un plug-in de contrôle de code source prend en charge plusieurs extractions (partagées), il déclare la `SCC_CAP_MULTICHECKOUT` fonctionnalité et implémente la `SccIsMultiCheckOutEnabled` fonction. Cette fonction est appelée chaque fois qu’une opération d’extraction se produit sur l’un des projets sous contrôle de code source.  
  
 Si un plug-in de contrôle de code source prend en charge la création et l’utilisation d’un MSSCCPRJ. Fichier SCC, puis déclare la `SCC_CAP_SCCFILE` fonctionnalité et implémente [SccWillCreateSccFile](../../extensibility/sccwillcreatesccfile-function.md). Cette fonction est appelée avec une liste de fichiers. La fonction retourne `TRUE/FALSE` pour chaque fichier pour indiquer si Visual Studio doit utiliser un Mssccprj. Fichier SCC pour celui-ci. Si le plug-in de contrôle de code source choisit de ne pas prendre en charge ces nouvelles fonctionnalités et fonctions, il peut utiliser la clé de Registre suivante pour désactiver la création de ces fichiers :  
  
 [HKEY_CURRENT_USER \Software\Microsoft\VisualStudio\8.0\SourceControl] "DoNotCreateTemporaryFilesInSourceControl" = dword : 00000001  
  
> [!NOTE]
> Si cette clé de Registre est définie sur DWORD : 00000000, elle est équivalente à la clé qui n’existe pas, et Visual Studio tente toujours de créer les fichiers temporaires. Toutefois, si la clé de Registre est définie sur DWORD : 00000001, Visual Studio ne tente pas de créer les fichiers temporaires. Au lieu de cela, il suppose que le plug-in de contrôle de code source ne prend pas en charge le MSSCCPRJ. Fichier SCC et ne prend pas en charge les extractions partagées.  
  
## <a name="see-also"></a>Voir aussi  
 [Nouveautés de l’API de plug-in de contrôle de code source version 1.2](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)
