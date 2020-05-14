---
title: Détection des exigences du système (en anglais seulement) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- setup, VSPackages
- launch conditions
ms.assetid: 0ba94acf-bf0b-4bb3-8cca-aaac1b5d6737
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9ab254df5d53f379704128d8860b8d7fe5655bae
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708733"
---
# <a name="detect-system-requirements"></a>Détecter les exigences du système
Un VSPackage ne peut fonctionner à moins que Visual Studio ne soit installé. Lorsque vous utilisez Microsoft Windows Installer pour gérer l’installation de votre VSPackage, vous pouvez configurer l’installateur pour détecter si Visual Studio est installé. Vous pouvez également le configurer pour vérifier le système pour d’autres exigences, par exemple, une version particulière de Windows ou une quantité particulière de RAM.

## <a name="detect-visual-studio-editions"></a>Détecter les éditions Visual Studio
 Pour déterminer si une édition de Visual Studio est installée, vérifiez que la valeur de la clé du registre **d’installation** est *(REG_DWORD) 1* dans le dossier approprié, tel que indiqué dans le tableau suivant. Notez qu’il existe une hiérarchie des éditions Visual Studio :

1. Entreprise

2. Professionnel

3. Communauté

Lorsqu’une nouvelle édition est installée, les clés du registre de cette édition sont ajoutées ainsi que pour les éditions précédentes. Autrement dit, si l’édition Enterprise est installée, la clé **d’installation** est définie à *1* pour l’entreprise, ainsi que pour les éditions Professionnelles et Communautaires. Par conséquent, vous devez vérifier uniquement pour l’édition la plus récente dont vous avez besoin.

> [!NOTE]
> Dans la version 64 bits de l’éditeur de registre, les touches 32 bits sont affichées sous **HKEY_LOCAL_MACHINE-SOFTWARE-Wow6432Node\\**. Les touches Visual Studio sont sous **HKEY_LOCAL_MACHINE-SOFTWARE-Wow6432Node-Microsoft-DevDivMD\\vs’Servicing**.

|Produit|Clé|
|-------------|---------|
|Visual Studio Enterprise 2015|HKEY_LOCAL_MACHINE-SOFTWARE-Microsoft-DevDivMD vs’Entretien'14.0'entreprise|
|Visual Studio Professional 2015|HKEY_LOCAL_MACHINE-SOFTWARE-Microsoft-DevDivMD vs’Entretien'14.0'professionnel|
|Visual Studio Community 2015|HKEY_LOCAL_MACHINE-SOFTWARE-Microsoft-DevDivMD vs’Entretien'14.0'communauté|
|Visual Studio 2015 Shell (intégré et isolé)|HKEY_LOCAL_MACHINE-SOFTWARE-Microsoft-DevDivMD vs’Entretien'14.0 'isoshell|

## <a name="detect-when-visual-studio-is-running"></a>Détecter quand Visual Studio est en cours d’exécution
 Votre VSPackage ne peut pas être enregistré correctement si Visual Studio est en cours d’exécution lorsque le VSPackage est installé. L’installateur doit détecter quand Visual Studio est en cours d’exécution, puis refuser d’installer le programme. Windows Install ne vous permet pas d’utiliser des entrées de table pour activer une telle détection. Au lieu de cela, vous devez créer `EnumProcesses` une action personnalisée, comme suit: Utilisez la fonction pour détecter le processus *devenv.exe,* puis soit définir une propriété installateur qui est utilisé dans un état de lancement ou afficher sous condition une boîte de dialogue qui invite l’utilisateur à fermer Visual Studio.

## <a name="see-also"></a>Voir aussi
- [Installer VSPackages Avec installateur Windows](../../extensibility/internals/installing-vspackages-with-windows-installer.md)
