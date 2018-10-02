---
title: Utilisation de différents navigateurs web avec des tests codés de l’interface utilisateur | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a859595f-6517-43f2-9d61-c706cb55a388
caps.latest.revision: 25
ms.author: gewarren
manager: douge
ms.openlocfilehash: 73fea4d5d3cccf90070e2e2a013684e2344205f5
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47504983"
---
# <a name="using-different-web-browsers-with-coded-ui-tests"></a>Utilisation de différents navigateurs Web avec des tests codés de l'interface utilisateur
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [à l’aide de différents navigateurs Web avec des Tests codés de l’interface utilisateur](https://docs.microsoft.com/visualstudio/test/using-different-web-browsers-with-coded-ui-tests).  
  
Les tests codés de l'interface utilisateur peuvent automatiser le test des applications web en enregistrant vos tests à l'aide d'Internet Explorer. Vous pouvez ensuite personnaliser votre test et l'utiliser à l'aide d'Internet Explorer ou d'autres types de navigateurs pour ces applications web.  
  
 **Spécifications**  
  
-   Visual Studio Enterprise  
  
-   Systèmes d'exploitation :  
  
    -   Microsoft Windows 7  
  
    -   Microsoft Windows 8  
  
    -   Microsoft Windows Server 2008 R2 SP1  
  
-   Versions de navigateur web :  
  
    -   Windows Internet Explorer 9  
  
    -   Windows Internet Explorer 10  
  
    -   Pour connaître les versions prises en charge de Mozilla Firefox et de Google Chrome, cliquez [ici](http://visualstudiogallery.msdn.microsoft.com/11cfc881-f8c9-4f96-b303-a2780156628d/).  
  
-   Installez les [composants Selenium pour les tests codés de l’interface utilisateur sur plusieurs navigateurs](http://visualstudiogallery.msdn.microsoft.com/11cfc881-f8c9-4f96-b303-a2780156628d/).  
  
 **Quelles sont les opérations prises en charge par tous les navigateurs web ?**  
  
-   [Ajouter du code personnalisé pour contrôler les fonctionnalités](http://blogs.msdn.com/b/visualstudioalm/archive/2012/12/10/coded-ui-test-configuring-search-properties-while-recording-on-internet-explorer.aspx) comme les propriétés, la recherche et les objets waiter de lecture.  
  
-   Boîtes de dialogue et menus contextuels  
  
-   [Exécuter le code JavaScript de base sans type de retour](http://blogs.msdn.com/b/visualstudioalm/archive/2013/01/18/introducing-jscript-execution-on-internetexplorer-and-crossbrowser-in-coded-ui-test.aspx)  
  
-   Résilience de recherche (avec concordance active) et [améliorations des performances](http://blogs.msdn.com/b/visualstudioalm/archive/2012/02/01/guidelines-on-improving-performance-of-coded-ui-test-playback.aspx)  
  
## <a name="why-should-i-use-coded-ui-tests-across-multiple-web-browser-types"></a>Pourquoi dois-je utiliser les tests codés de l'interface utilisateur sur différents types de navigateur web ?  
 Lorsque vous testez votre application web à l'aide de divers types de navigateurs web, l'expérience d'interface utilisateur des utilisateurs susceptibles d'utiliser des navigateurs différents est mieux émulée. Par exemple, votre application peut inclure un contrôle ou un code dans Internet Explorer qui n'est pas compatible avec d'autres navigateurs web. En exécutant les tests codés de l'interface utilisateur sur d'autres navigateurs, vous pouvez détecter et corriger les problèmes avant qu'ils aient une incidence sur vos clients.  
  
## <a name="how-do-i-record-and-play-back-coded-ui-tests-on-web-applications-using-the-supported-web-browsers"></a>Comment enregistrer et lire les tests d'interface utilisateur codés des applications web à l'aide des navigateurs web pris en charge ?  
 **Enregistrement :** vous devez utiliser le générateur de test codé de l’interface utilisateur pour enregistrer le test de votre application web à l’aide d’Internet Explorer. Vous pouvez éventuellement ajouter un code de validation personnalisé pour les contrôles testés à l’aide d’un jeu prédéfini de propriétés, de la même manière que pour les tests codés de l’interface utilisateur. Pour plus d’informations, consultez [Utiliser l’automatisation de l’interface utilisateur pour tester votre code](../test/use-ui-automation-to-test-your-code.md).  
  
> [!NOTE]
>  Vous ne pouvez pas enregistrer des tests codés de l'interface utilisateur à l'aide des navigateurs Google Chrome ou Mozilla Firefox.  
  
 **Lecture avec Internet Explorer :** lorsqu’aucun navigateur n’est explicitement spécifié, les tests s’exécutent par défaut sur Internet Explorer. Vous pouvez déclarer explicitement le navigateur à utiliser en définissant la propriété **BrowserWindow.CurrentBrowser** dans le code de votre test. Pour Internet Explorer, cette propriété doit être définie sur **IE** ou **Internet Explorer**.  
  
 **Lecture avec des navigateurs web autres qu’Internet Explorer** : pour lire sur les navigateurs web autres qu’Internet Explorer, modifiez la propriété BrowserWindow.CurrentBrowser dans votre code de test et définissez-la sur **Firefox** ou **Chrome**.  
  
 Pour lire les tests sur les navigateurs web autres qu’IE, vous devez installer les **composants Selenium pour les tests codés de l’interface utilisateur sur plusieurs navigateurs**.  
  
#### <a name="installing-selenium-components"></a>Installation des composants Selenium  
  
1.  Dans le menu **Outils** , choisissez **Extensions et mises à jour**.  
  
2.  Dans la boîte de dialogue Extensions et mises à jour, recherchez `Selenium components for Cross Browser Testing`.  
  
3.  Mettez en surbrillance l’extension et choisissez **Télécharger**.  
  
    > [!TIP]
    >  Vous pouvez également télécharger les composants Selenium pour le test codé de l’interface utilisateur sur plusieurs navigateurs [ici](http://visualstudiogallery.msdn.microsoft.com/11cfc881-f8c9-4f96-b303-a2780156628d/).  
  
 Pour plus d’informations sur la création et l’utilisation des tests codés de l’interface utilisateur, consultez [Création de tests codés de l’interface utilisateur](../test/use-ui-automation-to-test-your-code.md#VerifyingCodeUsingCUITCreate).  
  
### <a name="enable-debugging"></a>Activer le débogage  
 Pour activer le débogage de votre application web, vous devez utiliser les options de configuration suivantes :  
  
1.  Activer Uniquement mon code :  
  
    1.  Dans le menu **Outils**, choisissez **Options**, puis **Débogage**.  
  
    2.  Sélectionnez **Activer Uniquement mon code**.  
  
2.  Désactiver les exceptions CLR :  
  
    1.  Dans le menu **Déboguer**, choisissez **Exceptions**.  
  
    2.  Pour **Exceptions CLR**, désactivez **Non géré par l’utilisateur**.  
  
##  <a name="generate"></a> *Je ne vois pas l’option permettant de modifier BrowserWindow.CurrentBrowser dans le test codé de l’interface utilisateur.*  
 Vous utilisez peut-être une version de [!INCLUDE[vs2011_first](../includes/vs2011-first-md.md)] qui ne prend pas en charge les tests codés de l'interface utilisateur à l'aide de différents navigateurs web. Pour utiliser de tels tests codés de l’interface utilisateur, vous devez utiliser Visual Studio Enterprise.  
  
 *Que dois-je savoir de plus ?*  
 **Notes**  
  
-   ![Prérequis](../test/media/prereq.png "Prérequis") Le navigateur web Apple Safari n’est pas pris en charge.  
  
-   ![Prérequis](../test/media/prereq.png "Prérequis") L’action de démarrage du navigateur web doit faire partie du test codé de l’interface utilisateur.  
  
     Si un navigateur web est déjà ouvert et que vous souhaitez exécuter des étapes sur ce navigateur, la lecture échoue, sauf si vous utilisez Internet Explorer. Il est donc recommandé d'inclure le démarrage de votre navigateur web à vos tests codés de l'interface utilisateur.  
  
-   ![Prérequis](../test/media/prereq.png "Prérequis") L’automatisation d’actions d’interface utilisateur basées spécifiquement sur un navigateur, par exemple agrandir, réduire et restaurer, n’est pas prise en charge.  
  
 **Conseils**  
  
-   ![Conseil](../test/media/tip.png "Conseil") Vous pouvez configurer la sortie pour inclure des captures d’écran dans les journaux codés de l’interface utilisateur. Pour cela, vous devez définir des paramètres de configuration dans le fichier QTAgent32.exe.config. Par défaut, ce fichier est installé à l'endroit suivant :  
  
     **C:\Program Files (x86)\Microsoft Visual Studio 11.0\Common7\IDE**  
  
     Définissez les valeurs suivantes :  
  
    -   `EqtTraceLevel` dans la section `system.diagnostics`.  
  
    -   `<add name="EqtTraceLevel" value="4" />`  
  
         En affectant la valeur 3 ou une valeur supérieure, des captures sont prises pour chaque action. Lorsque la valeur est 1 ou 2, des captures sont prises uniquement pour les actions d'erreur.  
  
     Pour plus d’informations, consultez [Analyse des tests codés de l’interface utilisateur à l’aide des journaux de test codé de l’interface utilisateur](../test/analyzing-coded-ui-tests-using-coded-ui-test-logs.md).  
  
## <a name="external-resources"></a>Ressources externes  
  
### <a name="videos"></a>Vidéos  
 [Enregistrement dans IE et lecture dans tous les navigateurs](https://skydrive.live.com/redir?resid=AE5CD7309CCCC43C!183&authkey=!ANqaLtCZbtJrImU)  
  
 [Créer des tests multi-navigateurs avec le générateur de test codé de l’interface utilisateur](https://skydrive.live.com/redir?resid=AE5CD7309CCCC43C!184&authkey=!AKG8CSow_qmeTq8)  
  
 [Créer des tests multi-navigateurs avec du code brut sans mapper l’interface utilisateur](https://skydrive.live.com/redir?resid=AE5CD7309CCCC43C!186&authkey=!AJaEvxJnsefyAT4)  
  
 [Exécuter des tests multi-navigateurs de manière séquentielle sur plusieurs navigateurs](https://skydrive.live.com/redir?resid=AE5CD7309CCCC43C!187&authkey=!ADI8eCQkxHnpOR8)  
  
 [Résoudre les problèmes des tests multi-navigateurs](https://skydrive.live.com/redir?resid=AE5CD7309CCCC43C!182&authkey=!AEpS48i295B49FI)  
  
### <a name="guidance"></a>Conseils  
 [Test de la livraison continue avec Visual Studio 2012 - Chapitre 2 : Tests unitaires : tester l’intérieur](http://go.microsoft.com/fwlink/?LinkID=255188)  
  
 [Test de la livraison continue avec Visual Studio 2012 - Chapitre 5 : Automatisation des tests système](http://go.microsoft.com/fwlink/?LinkID=255196)  
  
### <a name="faq"></a>FAQ  
 [FAQ concernant les tests codés de l’interface utilisateur - 1](http://go.microsoft.com/fwlink/?LinkID=230576)  
  
 [FAQ concernant les tests codés de l’interface utilisateur - 2](http://go.microsoft.com/fwlink/?LinkID=230578)  
  
### <a name="forum"></a>Forum  
 [Visual Studio UI Automation Testing (avec tests codés de l’interface utilisateur)](http://go.microsoft.com/fwlink/?LinkID=224497)  
  
## <a name="see-also"></a>Voir aussi  
 [Utiliser UI Automation pour tester votre code](../test/use-ui-automation-to-test-your-code.md)   
 [Plateformes et configurations prises en charge pour les tests codés de l’interface utilisateur et les enregistrements des actions](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)   
 [Analyse des tests codés de l’interface utilisateur à l’aide des journaux de test codé de l’interface utilisateur](../test/analyzing-coded-ui-tests-using-coded-ui-test-logs.md)



