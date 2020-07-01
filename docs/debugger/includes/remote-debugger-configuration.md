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
ms.openlocfilehash: 2e5782c49f26925d9eda81f04653b1a20666c6b1
ms.sourcegitcommit: 748d9cd7328a30f8c80ce42198a94a4b5e869f26
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68149176"
---
1. Sur l’ordinateur distant, recherchez et démarrez le **débogueur distant** à partir du menu **Démarrer** . 
   
   Si vous ne disposez pas d’autorisations d’administration sur l’ordinateur distant, cliquez avec le bouton droit sur l’application du **débogueur distant** et sélectionnez **exécuter en tant qu’administrateur**. Dans le cas contraire, démarrez-le normalement.

   Si vous envisagez d’effectuer un attachement à un processus qui s’exécute en tant qu’administrateur ou s’il s’exécute sous un compte d’utilisateur différent (par exemple, IIS), cliquez avec le bouton droit sur l’application du **débogueur distant** et sélectionnez **exécuter en tant qu’administrateur**. Pour plus d’informations, consultez [exécuter le débogueur distant en tant qu’administrateur](../remote-debugging-errors-and-troubleshooting.md#run-the-remote-debugger-as-an-administrator).
   
1. La première fois que vous démarrez le débogueur distant (ou avant de le configurer), la boîte de dialogue **configuration du débogage distant** s’affiche.  
  
    (../media/remotedebuggerconfwizardpage.png "Configuration du débogueur distant") ![configuration du débogueur distant]  
  
1. Si l’API des services Web Windows n’est pas installée, ce qui se produit uniquement sur Windows Server 2008 R2, cliquez sur le bouton **installer** .  
  
1. Sélectionnez au moins un type de réseau sur lequel vous souhaitez utiliser les outils de contrôle à distance. Si les ordinateurs sont connectés à un domaine, vous devez choisir le premier élément. Si les ordinateurs sont connectés via un groupe de travail ou un groupe résidentiel, choisissez le deuxième ou le troisième élément, le cas échéant.  
  
1. Sélectionnez **configurer le débogage distant** pour configurer le pare-feu et démarrer le débogueur distant.  
  
1. Une fois la configuration terminée, la fenêtre du **débogueur distant** s’affiche.
  
    Fenêtre du débogueur ![distant fenêtre]du(../media/remotedebuggerwindow.png "débogueur distant")
  
    Le débogueur distant attend maintenant une connexion. Utilisez le nom du serveur et le numéro de port indiqués pour définir la configuration de la connexion à distance dans Visual Studio.  
  
Pour arrêter le débogueur distant, sélectionnez **fichier**  >  **quitter**. Vous pouvez le redémarrer à partir du menu **Démarrer** ou à partir de la ligne de commande :  
  
```cmd
<Remote debugger installation directory>\msvsmon.exe
```
