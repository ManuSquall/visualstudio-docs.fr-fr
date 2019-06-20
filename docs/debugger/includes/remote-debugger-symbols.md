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
ms.openlocfilehash: 26d9169be242990b9ca99b4fe4fe043d56fb7f30
ms.sourcegitcommit: b468d71052a1b8a697f477ab23a3644de139f1e9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2019
ms.locfileid: "67256172"
---
Vous devez pouvoir déboguer votre code avec les symboles que vous générez sur l’ordinateur Visual Studio. Les performances du débogueur distant sont nettement meilleures quand vous utilisez des symboles locaux.  Si vous devez utiliser des symboles distants, vous devez indiquer au Remote Debugging Monitor de rechercher les symboles sur l’ordinateur distant.  

À partir de Visual Studio 2013 Update 2, vous pouvez utiliser le commutateur de ligne de commande msvsmon suivant pour utiliser des symboles distants pour le code managé : `Msvsmon /FallbackLoadRemoteManagedPdbs`  

Pour plus d’informations, voir l’aide du débogage distant (appuyez sur **F1** dans la fenêtre du débogueur distant, ou cliquez sur **Aide > Utilisation**). D’autres informations sont disponibles dans [Modification du chargement des symboles distants .NET dans Visual Studio 2012 et 2013](http://blogs.msdn.com/b/visualstudioalm/archive/2013/10/16/net-remote-symbol-loading-changes-in-visual-studio-2012-and-2013.aspx).
