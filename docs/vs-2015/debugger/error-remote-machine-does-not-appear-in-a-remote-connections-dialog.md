---
title: 'Erreur : Ordinateur distant n’apparaît pas dans une boîte de dialogue connexions à distance | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 5fd98a5b-2cf3-4438-8b0f-6f1a742a62ce
caps.latest.revision: 5
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a86b7b639ab74d4b8df802b3b9086dcac19369d4
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58953407"
---
# <a name="error-remote-machine-does-not-appear-in-a-remote-connections-dialog"></a>Erreur : L’ordinateur distant n’apparaît pas dans une boîte de dialogue Connexions à distance
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Si l’ordinateur distant n’apparaît pas dans la boîte de dialogue Connexions à distance, vérifiez les causes courantes suivantes.  
  
 Si vous utilisez le mode de compatibilité managé, consultez la documentation de Visual Studio 2010 : [Résolution des problèmes du débogage distant - Visual Studio 2010](https://msdn.microsoft.com/library/2ys11ead\(v=vs.100\).aspx) .  
  
### <a name="common-causes-for-this-error"></a>Causes courantes de cette erreur  
  
-   L’ordinateur distant s’exécute sur un ordinateur qui se trouve dans un sous-réseau différent. Pour résoudre ce problème, tapez manuellement le nom ou l’adresse IP de l’ordinateur dans la boîte de dialogue Qualificateur  
  
-   Le débogueur distant ne fonctionne pas sur l’ordinateur distant. Pour résoudre ce problème, démarrez le débogueur distant.  
  
-   Le pare-feu bloque les communications entre Visual Studio et l’ordinateur distant. Pour résoudre ce problème, configurez votre pare-feu pour permettre à Visual Studio et au débogueur distant (msvsmon) de communiquer.  
  
-   Un logiciel antivirus bloque les communications entre Visual Studio et l’ordinateur distant. Pour résoudre ce problème, configurez le logiciel antivirus pour permettre à Visual Studio et au débogueur distant (msvsmon) de communiquer.  
  
## <a name="see-also"></a>Voir aussi  
 [Configurer les outils de contrôle à distance sur le périphérique](http://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c)
