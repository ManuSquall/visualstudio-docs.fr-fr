---
title: "Configuration système requise de détection | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- setup, VSPackages
- launch conditions
ms.assetid: 0ba94acf-bf0b-4bb3-8cca-aaac1b5d6737
caps.latest.revision: "50"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 92c4d51d575ffd6e5723bf80b8adc700b83f6afd
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="detecting-system-requirements"></a>Détecter la configuration système requise
Un VSPackage ne peut pas fonctionner que si Visual Studio est installé. Lorsque vous utilisez le programme d’installation de Microsoft Windows pour gérer l’installation de votre VSPackage, vous pouvez configurer le programme d’installation pour détecter si Visual Studio est installé. Vous pouvez également configurer pour rechercher le système pour les autres exigences, par exemple, une version particulière de Windows ou une quantité spécifique de mémoire vive.  
  
## <a name="detecting-visual-studio-editions"></a>Détection des éditions de Visual Studio  
 Pour déterminer si une édition de Visual Studio est installée, vérifiez que la valeur de la clé de Registre d’installation est (REG_DWORD) 1 dans le dossier approprié, comme indiqué dans le tableau suivant. Notez qu’il existe une hiérarchie des éditions de Visual Studio :  
  
1.  Entreprise  
  
2.  Professionnel  
  
3.  Communauté  
  
 Lorsqu’une édition « supérieure » est installée, les clés de Registre pour cette édition, ainsi que pour les éditions « inférieures » sont ajoutés. Autrement dit, si l’édition Enterprise est installée, la clé d’installation est définie sur 1 pour l’entreprise, ainsi que pour les éditions Professional et Communauté. Par conséquent, vous devez ne vérifier que pour l’édition « plus élevée », que vous avez besoin.  
  
> [!NOTE]
>  Dans la version 64 bits de l’Éditeur du Registre, les clés de 32 bits sont affichées sous HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\\. Les clés de Visual Studio sont sous HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\DevDiv\vs\Servicing\\.  
  
|Produit|Touche|  
|-------------|---------|  
|Visual Studio Enterprise 2015|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\DevDiv\vs\Servicing\14.0\enterprise|  
|Visual Studio Professional 2015|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\DevDiv\vs\Servicing\14.0\professional|  
|Visual Studio Community 2015|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\DevDiv\vs\Servicing\14.0\community|  
|Visual Studio 2015 Shell (intégré et isolé)|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\DevDiv\vs\Servicing\14.0\isoshell|  
  
## <a name="detecting-when-visual-studio-is-running"></a>Détection de Visual Studio est en cours d’exécution.  
 Impossible d’inscrire votre VSPackage correctement si Visual Studio est en cours d’exécution lorsque le package Visual Studio est installé. Le programme d’installation doit détecter lorsque Visual Studio est en cours d’exécution et refuser puis à installer le programme. Windows Installer ne vous permettent d’utiliser les entrées de table pour activer la détection de ce type. Au lieu de cela, vous devez créer une action personnalisée, comme suit : utilisez le `EnumProcesses` afin de détecter le processus devenv.exe et définissez une propriété du programme d’installation qui est utilisée dans une condition de lancement ou de manière conditionnelle soit afficher une boîte de dialogue qui invite l’utilisateur à fermer Visual Studio.  
  
## <a name="see-also"></a>Voir aussi  
 [Installation de VSPackages avec Windows Installer](../../extensibility/internals/installing-vspackages-with-windows-installer.md)