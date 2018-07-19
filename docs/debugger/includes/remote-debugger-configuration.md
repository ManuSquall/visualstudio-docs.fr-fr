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
ms.openlocfilehash: b6e312f7e1913a8b4533c0127b966dc3ac0d981d
ms.sourcegitcommit: c57ae28181ffe14a30731736661bf59c3eff1211
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2018
ms.locfileid: "38809259"
---
Vous devez disposer des autorisations administratives sur l’ordinateur distant.  
  
1.  Recherchez l’application du débogueur distant. (Recherchez msvsmon.exe dans l’emplacement où il a été installé ou ouvrez le menu Démarrer et recherchez **débogueur distant**.)
  
     Si vous exécutez le débogueur distant sur un serveur distant, vous pouvez avec le bouton droit de l’application débogueur distant et choisissez **exécuter en tant qu’administrateur**. Si vous n’exécutez pas sur un serveur distant, seulement le démarrer normalement.
  
3.  Lorsque vous démarrez les outils à distance pour la première fois (ou avant que vous l’avez configuré), le **Configuration du débogage distant** boîte de dialogue s’affiche.  
  
     ![RemoteDebuggerConfWizardPage](../media/remotedebuggerconfwizardpage.png "RemoteDebuggerConfWizardPage")  
  
4.  Si l’API de Service Windows n’est pas installé (ce qui se produit uniquement sur Windows Server 2008 R2), choisissez le **installer** bouton.  
  
5.  Sélectionnez les types de réseau sur lesquels vous voulez utiliser les outils de contrôle à distance. Au moins un type de réseau doit être sélectionné. Si les ordinateurs sont connectés à un domaine, vous devez choisir le premier élément. Si les ordinateurs sont connectés à un groupe de travail ou un groupe résidentiel, vous devez choisir le deuxième ou troisième élément, selon les besoins.  
  
6.  Choisissez **configurer le débogage distant** pour configurer le pare-feu et démarrer l’outil.  
  
7.  Une fois la configuration terminée, la fenêtre du débogueur distant s’affiche.
  
     ![RemoteDebuggerWindow](../media/remotedebuggerwindow.png "RemoteDebuggerWindow")
  
     Le débogueur distant est maintenant en attente pour une connexion. Prenez note du nom du serveur et le port numéro qui s’affiche, car il doit correspondre à la configuration que vous utilisez plus tard dans Visual Studio.  
  
 Lorsque vous avez terminé le débogage et vous devez arrêter le débogueur distant, cliquez sur **fichier > sortie** dans la fenêtre. Vous pouvez le redémarrer à partir de la **Démarrer** menu ou à partir de la ligne de commande :  
  
 **\<Répertoire d’installation de débogueur distant >\\< x86, x64, ARM, ARM64 ou Appx > \msvsmon.exe**.  
