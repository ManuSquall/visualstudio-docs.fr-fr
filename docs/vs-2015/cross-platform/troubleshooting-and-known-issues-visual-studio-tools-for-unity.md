---
title: Problèmes connus et dépannage (Visual Studio Tools pour Unity) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-unity-tools
ms.topic: troubleshooting
ms.assetid: 8f5db192-8d78-4627-bd07-dbbc803ac554
caps.latest.revision: 7
author: conceptdev
ms.author: crdun
manager: jillfra
ms.openlocfilehash: ad085cc6c41714a551fbb344274e6d0f164ab67e
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74297658"
---
# <a name="troubleshooting-and-known-issues-visual-studio-tools-for-unity"></a>Problèmes connus et dépannage (Visual Studio Tools pour Unity)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Dans cette section, vous allez trouver les solutions aux problèmes courants rencontrés par Visual Studio Tools pour Unity, ainsi que la description de problèmes identifiés. Vous apprendrez aussi comment vous pouvez aider à améliorer Visual Studio Tools pour Unity en signalant les erreurs.  
  
## <a name="troubleshooting"></a>Résolution des problèmes  
 Pour résoudre certains problèmes courants avec Visual Studio Tools pour Unity, consultez les sections suivantes.  
  
### <a name="migrating-from-unityvs-to-visual-studio-tools-for-unity"></a>Migration de UnityVS vers Visual Studio Tools pour Unity  
 Si vous procédez à une migration à partir de UnityVS vers Visual Studio Tools pour Unity, vous devez générer de nouvelles solutions Visual Studio pour vos projets Unity.  
  
##### <a name="to-migrate-your-unity-project-from-unityvs-18-to-visual-studio-tools-for-unity-19"></a>Pour migrer votre projet Unity de UnityVS 1.8 vers Visual Studio Tools pour Unity 1.9  
  
1. Supprimez les anciens fichiers solution et projet de votre projet Unity. Dans le répertoire racine de votre projet Unity, recherchez les fichiers Visual Studio .sln et *.proj, puis supprimez-les.  
  
2. Importez le package Visual Studio Tools pour Unity dans votre projet Unity. Pour plus d'informations sur l'importation du package VSTU, consultez Configurer Visual Studio Tools pour Unity dans la page [Prise en main](../cross-platform/getting-started-with-visual-studio-tools-for-unity.md) .  
  
3. Générez les nouveaux fichiers solution et projet. Si vous souhaitez les générer maintenant, dans l'éditeur Unity, dans le menu principal, choisissez **Visual Studio Tools**, **Générer les fichiers projet**. Sinon, vous pouvez ignorer cette étape si vous le souhaitez. Visual Studio Tools pour Unity génère les nouveaux fichiers automatiquement lorsque vous choisissez **Visual Studio Tools**, **Ouvrir dans Visual Studio**.  
  
### <a name="visual-studio-wont-load-the-solution-that-visual-studio-tools-for-unity-created"></a>Visual Studio ne charge pas la solution que Visual Studio Tools pour Unity a créée  
 Pour plus d’informations, consultez [la réponse à cette question sur stackoverflow](https://stackoverflow.com/questions/20086755/unityvs-visual-studio-can-not-open/24035907#24035907).  
  
### <a name="on-windows-8-visual-studio-asks-to-download-the-unity-target-framework"></a>Dans Windows 8, Visual Studio vous demande de télécharger le framework cible Unity.  
 UnityVS a besoin de .Net Framework 3.5, qui n’est pas installé par défaut sur Windows 8. Pour résoudre ce problème, suivez les instructions de téléchargement et d’installation de .Net Framework 3.5.  
  
## <a name="known-issues"></a>Problèmes connus  
 Il existe des problèmes connus dans Visual Studio Tools pour Unity qui résultent de la façon dont le débogueur interagit avec une version antérieure de Unity du compilateur C#. Nous nous efforçons de vous aider à résoudre ces problèmes, mais vous rencontrerez peut-être les problèmes suivants d'ici-là.  
  
- Lors du débogage, il arrive que Unity s'arrête.  
  
- Lors du débogage, il arrive que Unity se bloque.  
  
- L'exécution pas à pas et la reprise des méthodes ne fonctionnent parfois pas très bien, en particulier dans les itérateurs ou dans les instructions switch.  
  
## <a name="reporting-errors"></a>Signalement des erreurs  
 Aidez-nous à améliorer la qualité de Visual Studio Tools for Unity en envoyant des rapports d'erreurs lorsque vous êtes confronté à un arrêt, un blocage ou autres erreurs. Ceci nous permet d'examiner et de résoudre les problèmes de Visual Studio Tools pour Unity. Merci  
  
### <a name="how-to-report-an-error-when-visual-studio-freezes"></a>Comment signaler une erreur lorsque Visual Studio se bloque  
 Il a été établi que Visual Studio se bloque parfois lors du débogage avec Visual Studio Tools pour Unity, mais nous avons besoin de plus de données pour comprendre ce problème. Vous pouvez nous aider à enquêter sur le problème en suivant les étapes ci-dessous.  
  
##### <a name="to-report-that-visual-studio-freezes-while-debugging-with-visual-studio-tools-for-unity"></a>Pour signaler que Visual Studio se bloque pendant le débogage avec Visual Studio Tools pour Unity  
  
1. Ouvrez une nouvelle instance de Visual Studio.  
  
2. Ouvrez la boîte de dialogue Attacher au processus. Dans la nouvelle instance de Visual Studio, dans le menu principal, choisissez **Déboguer**, **Attacher au processus**.  
  
3. Attachez le débogueur à l'instance figée de Visual Studio. Dans la boîte de dialogue **Attacher au processus** , sélectionnez l'instance figée de Visual Studio à partir de la table **Processus disponibles** , puis choisissez le bouton **Attacher** .  
  
4. Interrompez le débogueur. Dans la nouvelle instance de Visual Studio, dans le menu principal, choisissez **Déboguer**, **Interrompre tout** ou appuyez simplement sur **Ctrl+Alt+Pause**  
  
5. Créez un vidage de thread. Dans la fenêtre Commande, entrez la commande suivante et appuyez sur **Entrée**.  
  
   ```powershell  
   Debug.ListCallStack /AllThreads /ShowExternalCode  
   ```  
  
    Vous devrez peut-être afficher d'abord la fenêtre **Commande** . Dans Visual Studio, dans le menu principal, choisissez **Affichage**, **Autres fenêtres**, **Fenêtre Commande**.  
  
6. Enfin, envoyez le vidage de thread à [vstusp@microsoft.com](mailto:vstusp@microsoft.com), ainsi qu’une description de ce que vous faisiez quand Visual Studio s’est bloqué.
