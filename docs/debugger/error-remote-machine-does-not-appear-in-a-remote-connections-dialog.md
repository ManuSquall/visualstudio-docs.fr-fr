---
title: 'Erreur : Ordinateur distant n’apparaît pas dans une boîte de dialogue connexions à distance | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: troubleshooting
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c52a2ebd99b052171220fd8a06f1ae7ff5dc258e
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2018
ms.locfileid: "31471331"
---
# <a name="error-remote-machine-does-not-appear-in-a-remote-connections-dialog"></a>Erreur : l’ordinateur distant n’apparaît pas dans une boîte de dialogue Connexions à distance
Si l’ordinateur distant n’apparaît pas dans la boîte de dialogue Connexions à distance, vérifiez les causes courantes suivantes.  
  
 Si vous utilisez le mode de compatibilité managé, consultez la documentation de Visual Studio 2010 : [Dépannage du débogage distant - Visual Studio 2010](https://msdn.microsoft.com/en-us/library/2ys11ead\(v=vs.100\).aspx) .  
  
### <a name="common-causes-for-this-error"></a>Causes courantes de cette erreur  
  
-   L’ordinateur distant s’exécute sur un ordinateur qui se trouve dans un sous-réseau différent. Pour résoudre ce problème, tapez manuellement le nom ou l’adresse IP de l’ordinateur dans la boîte de dialogue Qualificateur  
  
-   Le débogueur distant ne fonctionne pas sur l’ordinateur distant. Pour résoudre ce problème, démarrez le débogueur distant.  
  
-   Le pare-feu bloque les communications entre Visual Studio et l’ordinateur distant. Pour résoudre ce problème, configurez votre pare-feu pour permettre à Visual Studio et au débogueur distant (msvsmon) de communiquer.  
  
-   Un logiciel antivirus bloque les communications entre Visual Studio et l’ordinateur distant. Pour résoudre ce problème, configurez le logiciel antivirus pour permettre à Visual Studio et au débogueur distant (msvsmon) de communiquer.  
  
## <a name="see-also"></a>Voir aussi  
 [Débogage à distance](../debugger/remote-debugging.md)