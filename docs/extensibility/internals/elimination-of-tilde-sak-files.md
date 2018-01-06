---
title: "Élimination de ~ SAK fichiers | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- temporary files
- ~sak files
- source control plug-ins, ~SAK files
ms.assetid: 5277b5fa-073b-4bd1-8ba1-9dc913aa3c50
caps.latest.revision: "15"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 8d72a42c89cc775b9312d301a052ee102d977728
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="elimination-of-sak-files"></a>Élimination de ~ SAK fichiers
Dans la Source de contrôle du plug-in API 1.2, le ~ les fichiers SAK ont été remplacés par des indicateurs de fonctionnalité et de nouvelles fonctions de détecter si un plug-in de contrôle de code source prend en charge le fichier MSSCCPRJ et les extractions partagées.  
  
## <a name="sak-files"></a>~ Les fichiers SAK  
 Visual Studio .NET 2003 créé des fichiers temporaires avec le préfixe ~ SAK. Ces fichiers sont utilisés pour déterminer si un plug-in de contrôle de code source prend en charge :  
  
-   Le MSSCCPRJ. Fichier de contrôle de code source.  
  
-   Extractions multiples (partagées).  
  
 Les plug-ins qui prennent en charge les fonctions avancées fournies dans le 1.2 de API de plug-in de contrôle Source, l’IDE peut détecter ces capacités sans créer les fichiers temporaires à l’aide des nouvelles fonctionnalités, des indicateurs et des fonctions, détaillées dans les sections suivantes.  
  
## <a name="new-capability-flags"></a>Nouveaux indicateurs de capacité  
 `SCC_CAP_SCCFILE`  
  
 `SCC_CAP_MULTICHECKOUT`  
  
## <a name="new-functions"></a>Nouvelles fonctions  
 [SccWillCreateSccFile](../../extensibility/sccwillcreatesccfile-function.md)  
  
 [SccIsMultiCheckoutEnabled](../../extensibility/sccismulticheckoutenabled-function.md)  
  
 Si un plug-in de contrôle de code source prend en charge les extractions multiples (partagées), puis il déclare le `SCC_CAP_MULTICHECKOUT` fonctionnalité et met en œuvre le `SccIsMultiCheckOutEnabled` (fonction). Cette fonction est appelée chaque fois qu’une opération d’extraction se produit sur un des projets sous contrôle de code source.  
  
 Si un plug-in de contrôle de code source prend en charge la création et l’utilisation d’un MSSCCPRJ. Le fichier de contrôle de code source, puis il déclare le `SCC_CAP_SCCFILE` fonctionnalité et met en œuvre la [SccWillCreateSccFile](../../extensibility/sccwillcreatesccfile-function.md). Cette fonction est appelée avec une liste de fichiers. La fonction retourne `TRUE/FALSE` pour chaque fichier indiquer si Visual Studio doit utiliser un MSSCCPRJ. Fichier de contrôle de code source pour celle-ci. Si le plug-in de contrôle de code source choisit de ne pas prendre en charge ces nouvelles fonctionnalités et les fonctions, il peut utiliser la clé de Registre suivante pour désactiver la création de ces fichiers :  
  
 [HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl] « DoNotCreateTemporaryFilesInSourceControl » = DWORD : 00000001  
  
> [!NOTE]
>  Si cette clé de Registre a la valeur DWORD : 00000000, elle est équivalente à la clé en cours qui n’existe pas, et tente toujours de Visual Studio créer les fichiers temporaires. Toutefois, si la clé de Registre a la valeur DWORD : 00000001, Visual Studio n’essaie pas de créer les fichiers temporaires. Au lieu de cela, il suppose que le plug-in de contrôle de code source ne prend pas en charge la MSSCCPRJ. Fichier de contrôle de code source et ne prend pas en charge les extractions partagées.  
  
## <a name="see-also"></a>Voir aussi  
 [Nouveautés dans l’API de plug-in de contrôle de code source version 1.2](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)