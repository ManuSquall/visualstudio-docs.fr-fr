---
title: Détection de la configuration système requise | Microsoft Docs
description: Découvrez comment configurer le Microsoft Windows Installer pour détecter la configuration système requise, telle que l’édition de Visual Studio installée.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- setup, VSPackages
- launch conditions
ms.assetid: 0ba94acf-bf0b-4bb3-8cca-aaac1b5d6737
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 20287ba123c5736c9eb7077622623f4a739bde5c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99963469"
---
# <a name="detect-system-requirements"></a>Détecter la configuration système requise
Un VSPackage ne peut pas fonctionner tant que Visual Studio n’est pas installé. Lorsque vous utilisez Microsoft Windows Installer pour gérer l’installation de votre VSPackage, vous pouvez configurer le programme d’installation pour détecter si Visual Studio est installé. Vous pouvez également le configurer pour vérifier le système à la recherche d’autres exigences, par exemple, une version particulière de Windows ou une quantité spécifique de RAM.

## <a name="detect-visual-studio-editions"></a>Détecter les éditions de Visual Studio
 Pour déterminer si une édition de Visual Studio est installée, vérifiez que la valeur de la clé de Registre **install** est *(REG_DWORD) 1* dans le dossier approprié, comme indiqué dans le tableau suivant. Notez qu’il existe une hiérarchie d’éditions de Visual Studio :

1. Enterprise

2. Professional

3. Communauté

Lors de l’installation d’une édition plus récente, les clés de registre de cette édition sont ajoutées, ainsi que pour les éditions antérieures. Autrement dit, si l’édition Enterprise est installée, la clé d' **installation** est définie sur *1* pour Enterprise, ainsi que pour les éditions Professional et Community. Par conséquent, vous devez vérifier uniquement l’édition la plus récente dont vous avez besoin.

> [!NOTE]
> Dans la version 64 bits de l’éditeur du Registre, les clés 32 bits sont affichées sous **HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\\**. Les clés Visual Studio sont sous **HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\DevDiv\vs\Servicing\\**.

|Produit|Clé|
|-------------|---------|
|Visual Studio Enterprise 2015|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\DevDiv\vs\Servicing\14.0\enterprise|
|Visual Studio Professional 2015|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\DevDiv\vs\Servicing\14.0\professional|
|Visual Studio Community 2015|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\DevDiv\vs\Servicing\14.0\community|
|Visual Studio 2015 Shell (intégré et isolé)|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\DevDiv\vs\Servicing\14.0\isoshell|

## <a name="detect-when-visual-studio-is-running"></a>Détecter quand Visual Studio est en cours d’exécution
 Votre VSPackage ne peut pas être inscrit correctement si Visual Studio est en cours d’exécution lors de l’installation du VSPackage. Le programme d’installation doit détecter quand Visual Studio est en cours d’exécution, puis refuser d’installer le programme. Windows Installer ne vous permet pas d’utiliser des entrées de table pour activer une telle détection. Au lieu de cela, vous devez créer une action personnalisée, comme suit : utilisez la `EnumProcesses` fonction pour détecter le processus de *devenv.exe* , puis définissez une propriété de programme d’installation qui est utilisée dans une condition de lancement ou affichez une boîte de dialogue de manière conditionnelle pour inviter l’utilisateur à fermer Visual Studio.

## <a name="see-also"></a>Voir aussi
- [Installer les VSPackages avec Windows Installer](../../extensibility/internals/installing-vspackages-with-windows-installer.md)
