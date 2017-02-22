---
title: "D&#233;tecter la configuration syst&#232;me requise | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "installation, VSPackages"
  - "conditions de lancement"
ms.assetid: 0ba94acf-bf0b-4bb3-8cca-aaac1b5d6737
caps.latest.revision: 50
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 50
---
# D&#233;tecter la configuration syst&#232;me requise
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Un VSPackage ne peut pas fonctionner que si Visual Studio est installé. Lorsque vous utilisez le programme d’installation de Microsoft Windows pour gérer l’installation de votre package VS, vous pouvez configurer le programme d’installation pour détecter si Visual Studio est installé. Vous pouvez également configurer pour vérifier si le système pour les autres exigences, par exemple, une version particulière de Windows ou une quantité spécifique de mémoire vive.  
  
## Détection des éditions de Visual Studio  
 Pour déterminer si une édition de Visual Studio est installée, vérifiez que la valeur de la clé de Registre d’installation est \(REG\_DWORD\) 1 dans le dossier approprié, tel que répertorié dans le tableau suivant. Notez qu’il existe une hiérarchie des éditions de Visual Studio :  
  
1.  Entreprise  
  
2.  Professionnel  
  
3.  Communauté  
  
 Lorsqu’une version « supérieure » est installée, les clés de Registre pour cette édition, ainsi que pour les éditions « inférieures » sont ajoutés. Autrement dit, si l’édition entreprise est installée, la clé d’installation est définie sur 1 pour l’entreprise, ainsi que les éditions Professional et Communauté. Par conséquent, vous devez ne vérifier que pour l’édition « plus élevée », que vous avez besoin.  
  
> [!NOTE]
>  Dans la version 64 bits de l’Éditeur du Registre, les clés 32 bits sont affichent sous HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Wow6432Node\\. Les clés de Visual Studio sont sous HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Wow6432Node\\Microsoft\\DevDiv\\vs\\Servicing\\.  
  
|Produit|Clé|  
|-------------|---------|  
|Visual Studio Enterprise 2015|HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\DevDiv\\vs\\Servicing\\14.0\\enterprise|  
|Visual Studio Professional 2015|HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\DevDiv\\vs\\Servicing\\14.0\\professional|  
|Visual Studio Community 2015|HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\DevDiv\\vs\\Servicing\\14.0\\community|  
|Visual Studio 2015 Shell \(intégré et isolé\)|HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\DevDiv\\vs\\Servicing\\14.0\\isoshell|  
  
## Détection de Visual Studio est en cours d’exécution.  
 Votre VSPackage ne peut pas être correctement inscrit si Visual Studio est en cours d’exécution lorsque le VSPackage est installé. Le programme d’installation doit détecter lorsque Visual Studio est en cours d’exécution et refuser puis à installer le programme. Windows Installer ne vous permettent d’utiliser les entrées de la table pour activer la détection de ce type. Au lieu de cela, vous devez créer une action personnalisée, comme suit : utilisez le `EnumProcesses` fonction pour détecter le processus devenv.exe et définissez une propriété du programme d’installation qui est utilisée dans une condition de lancement ou de manière conditionnelle soit afficher une boîte de dialogue qui invite l’utilisateur à fermer Visual Studio.  
  
## Voir aussi  
 [Installation de packages VS avec Windows Installer](../../extensibility/internals/installing-vspackages-with-windows-installer.md)