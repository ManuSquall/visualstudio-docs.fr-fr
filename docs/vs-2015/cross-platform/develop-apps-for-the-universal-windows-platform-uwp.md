---
title: Développer des applications pour la plateforme Windows universelle (UWP) | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- tgt-pltfrm-cross-plat
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: eac59cb6-f12e-4a77-9953-6d62b164a643
caps.latest.revision: 50
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 24dfca5d4ac8432cbe659bb42ca54d0398c47c04
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51766473"
---
# <a name="develop-apps-for-the-universal-windows-platform-uwp"></a>Développer des applications pour la plateforme Windows universelle (UWP)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Avec la plateforme Windows universelle et notre noyau Windows, vous pouvez exécuter la même application sur n’importe quel appareil Windows 10, des téléphones jusqu’aux ordinateurs de bureau. Créez ces applications Windows universelles avec Visual Studio 2015 et les outils de développement d’applications Windows universelles.  
  
 ![Plateforme Windows universelle](../cross-platform/media/uwp-coreextensions.png "UWP_CoreExtensions")  
  
 Exécutez votre application sur un téléphone Windows 10, un poste de travail Windows 10 ou une console Xbox. C’est le même package d’application ! Avec l’introduction d’un noyau unifié unique dans Windows 10, le même package d’application peut s’exécuter sur toutes les plateformes. Plusieurs plateformes ont des kits de développement logiciel (SDK) Extension que vous pouvez ajouter à votre application pour tirer parti des comportements spécifiques à une plateforme. Par exemple, un SDK d’extension pour mobile gère le comportement du bouton Précédent sur un Windows Phone. Si vous référencez un SDK d’extension dans votre projet, il vous suffit ensuite d’ajouter des vérifications à l’exécution pour vérifier si ce SDK est disponible sur cette plateforme. C’est comme cela que vous pouvez utiliser le même package d’application pour toutes les plateformes !  
  
 **Qu’est-ce que le noyau de Windows ?**  
  
 Pour la première fois, Windows a été refactorisé pour avoir un noyau commun sur toutes les plateformes Windows 10. Il y a donc maintenant un code source commun, un noyau Windows commun, une seule pile d’E/S de fichier et un modèle d’application unique. Pour l’interface utilisateur, il y a seulement une infrastructure d’interface utilisateur XAML et une infrastructure d’interface utilisateur HTML. Ainsi, vous pouvez vous concentrer sur la création de l’application proprement dit, car nous avons fait en sorte qu’il soit facile de l’exécuter sur différents appareils Windows 10.  
  
 **Qu’est-ce que la plateforme Windows universelle plus précisément ?**  
  
 C’est tout simplement un ensemble de contrats et de versions, qui vous permettent de choisir les cibles d’exécution de votre application. Vous ne ciblez plus un système d’exploitation. À présent, vous ciblez votre application sur une ou plusieurs familles d’appareils. En savoir plus grâce à ce [guide de plateforme](http://msdn.microsoft.com/library/windows/apps/dn894631.aspx).  
  
## <a name="requirements"></a>Configuration requise  
 Les outils de développement d’applications Windows universelles sont fournis avec des émulateurs qui vous permettent de vérifier l’apparence de votre application sur différents appareils. Si vous souhaitez utiliser ces émulateurs, vous devez installer ce logiciel sur un ordinateur physique. L’ordinateur physique doit exécuter Windows 8.1 (x64) Professionnel ou une version ultérieure, et être équipé d’un processeur qui prend en charge Hyper-V Client et la conversion SLAT (Second Level Address Translation). Vous ne pouvez pas utiliser les émulateurs quand Visual Studio est installé sur un ordinateur virtuel.  
  
 Voici la liste des logiciels dont vous avez besoin :  
  
- [Windows 10](http://windows.microsoft.com/windows/downloads)  
  
- [Visual Studio 2015](http://go.microsoft.com/fwlink/p/?LinkId=526725). Assurez-vous que les outils de développement d’applications Windows universelles sont sélectionnés dans la liste des fonctionnalités facultatives. Sans ces outils, vous ne pourrez pas créer d’applications universelles.  
  
  Après avoir installé ce logiciel, vous devez [activer votre appareil Windows 10](https://msdn.microsoft.com/library/windows/apps/xaml/dn706236.aspx) pour le développement. (Vous n’avez plus besoin d’une licence de développeur par appareil Windows 10.)  
  
  **Prise en charge de Windows 8.1 et Windows 7**  
  
  Si vous choisissez de développer des applications Windows universelles avec Visual Studio 2015 sur une plateforme autre que Windows 10, voici les restrictions :  
  
- Windows 8.1 : vous ne pouvez pas exécuter l’application localement (uniquement sur un appareil Windows 10 distant). Vous pouvez utiliser les émulateurs dans Visual Studio, mais pas le simulateur.  
  
- Windows 7 : vous ne pouvez pas exécuter l’application localement (uniquement sur un appareil Windows 10 distant). Vous ne pouvez pas non plus utiliser les émulateurs ou le simulateur dans Visual Studio.  
  
  Vous pouvez utiliser le concepteur XAML uniquement si votre plateforme de développement est Windows 10.  
  
## <a name="universal-windows-apps"></a>Applications pour la plateforme Windows universelle  
 Choisissez votre langage de développement préféré entre C#, Visual Basic, C++ ou JavaScript pour [créer une application Windows universelle pour les appareils Windows 10](http://msdn.microsoft.com/library/windows/apps/xaml/dn609832.aspx#target_win10). Vous pouvez aussi regarder [cette vidéo de prise en main](http://channel9.msdn.com/Series/ConnectOn-Demand/229).  
  
 Si vous avez des applications Windows Store 8.1, des applications Windows Phone 8.1 ou des applications Windows universelles créées à l’aide de Visual Studio 2015 RC, [portez ces applications existantes](http://msdn.microsoft.com/library/windows/apps/xaml/mt238321.aspx) afin d’utiliser la dernière plateforme Windows universelle.  
  
 Après avoir créé votre application Windows universelle, vous devez [l’empaqueter](https://msdn.microsoft.com/library/windows/apps/hh454036.aspx) pour l’installer sur un appareil Windows 10 ou la soumettre au Windows Store.

