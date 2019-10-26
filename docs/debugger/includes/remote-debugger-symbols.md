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
ms.openlocfilehash: 5033580f253a5eb42cbc64656e8c4661a2e246c1
ms.sourcegitcommit: 257fc60eb01fefafa9185fca28727ded81b8bca9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/25/2019
ms.locfileid: "72912846"
---
Vous devez pouvoir déboguer votre code avec les symboles que vous générez sur l’ordinateur Visual Studio. Les performances du débogueur distant sont nettement meilleures quand vous utilisez des symboles locaux.  Si vous devez utiliser des symboles distants, vous devez indiquer au Remote Debugging Monitor de rechercher les symboles sur l’ordinateur distant.  

À partir de Visual Studio 2013 Update 2, vous pouvez utiliser le commutateur de ligne de commande msvsmon suivant pour utiliser des symboles distants pour le code managé : `Msvsmon /FallbackLoadRemoteManagedPdbs`  

Pour plus d’informations, voir l’aide du débogage distant (appuyez sur **F1** dans la fenêtre du débogueur distant, ou cliquez sur **Aide > Utilisation**). D’autres informations sont disponibles dans [Modification du chargement des symboles distants .NET dans Visual Studio 2012 et 2013](https://devblogs.microsoft.com/devops/net-remote-symbol-loading-changes-in-visual-studio-2012-and-2013/).
