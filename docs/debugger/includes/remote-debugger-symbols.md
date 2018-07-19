---
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.openlocfilehash: 95d76781f651b681b81e4dd18848b404d8a85664
ms.sourcegitcommit: c57ae28181ffe14a30731736661bf59c3eff1211
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2018
ms.locfileid: "38809252"
---
 Vous devez pouvoir déboguer votre code avec les symboles que vous générez sur l’ordinateur Visual Studio. Les performances du débogueur distant sont nettement meilleures quand vous utilisez des symboles locaux.  Si vous devez utiliser des symboles distants, vous devez indiquer au Remote Debugging Monitor de rechercher les symboles sur l’ordinateur distant.  
  
 À partir de Visual Studio 2013 Update 2, vous pouvez utiliser le commutateur de ligne de commande msvsmon suivant pour utiliser des symboles distants pour le code managé : `Msvsmon /FallbackLoadRemoteManagedPdbs`  
  
 Pour plus d’informations, consultez l’aide du débogage distant (appuyez sur **F1** dans la fenêtre du débogueur distant, ou cliquez sur **aide > utilisation**). Vous trouverez plus d’informations sur [modifications symboles distants .NET le chargement dans Visual Studio 2012 et 2013](http://blogs.msdn.com/b/visualstudioalm/archive/2013/10/16/net-remote-symbol-loading-changes-in-visual-studio-2012-and-2013.aspx)