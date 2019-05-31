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
ms.openlocfilehash: d89dbc0b752c2b8c538ec53769c166b6edbd802f
ms.sourcegitcommit: 2ee11676af4f3fc5729934d52541e9871fb43ee9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/17/2019
ms.locfileid: "65839821"
---
1. Sur l’ordinateur distant, rechercher et démarrer le **débogueur distant** à partir de la **Démarrer** menu. 
   
   Si vous n’avez les autorisations administratives sur l’ordinateur distant, cliquez sur le **débogueur distant** application et sélectionnez **exécuter en tant qu’administrateur**. Sinon, simplement démarrer normalement.

   Il peut y avoir différentes versions de *msvsmon.exe* dans *x64*, *x32*, ou d’autres dossiers. Veillez à démarrer la version que vous avez besoin déboguer votre application. 
   
1. La première fois que vous démarrez le débogueur distant (ou avant que vous l’avez configuré), le **Configuration du débogage distant** boîte de dialogue s’affiche.  
  
    ![Configuration du débogueur distant](../media/remotedebuggerconfwizardpage.png "configuration du débogueur distant")  
  
1. Si l’API des Services Web Windows n’est pas installé, ce qui se produit uniquement sur Windows Server 2008 R2, sélectionnez le **installer** bouton.  
  
1. Sélectionnez au moins un type de réseau à utiliser les outils à distance sur. Si les ordinateurs sont connectés à un domaine, vous devez choisir le premier élément. Si les ordinateurs sont connectés à un groupe de travail ou un groupe résidentiel, choisissez la deuxième ou troisième élément comme il convient.  
  
1. Sélectionnez **configurer le débogage distant** pour configurer le pare-feu et démarrer le débogueur distant.  
  
1. Lors de la configuration est terminée, le **débogueur distant** fenêtre s’affiche.
  
    ![Fenêtre du débogueur distante](../media/remotedebuggerwindow.png "fenêtre du débogueur distant")
  
    Le débogueur distant est maintenant en attente pour une connexion. Utiliser le nom du serveur et le port numéro indiqué pour définir la configuration de la connexion à distance dans Visual Studio.  
  
Pour arrêter le débogueur distant, sélectionnez **fichier** > **Exit**. Vous pouvez le redémarrer à partir de la **Démarrer** menu, ou à partir de la ligne de commande :  
  
```cmd
<Remote debugger installation directory>\msvsmon.exe
```
