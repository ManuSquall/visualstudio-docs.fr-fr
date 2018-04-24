---
title: Résoudre les points d’arrêt dans le débogueur Visual Studio | Documents Microsoft
ms.custom: ''
ms.date: 01/23/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d587809a9690e312e923ba184c9d90c38405a5d6
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2018
---
# <a name="troubleshoot-breakpoints-in-the-visual-studio-debugger"></a>Résoudre les points d’arrêt dans le débogueur Visual Studio

## <a name="breakpoint-warnings"></a>Avertissements de point d’arrêt

Lors du débogage, un point d’arrêt a deux états visuels possible : un cercle rouge uni et des creux (blanc remplie) cercle. Si le débogueur ne peut correctement définir un point d’arrêt dans le processus cible, il reste un cercle rouge uni. Si le point d’arrêt est un cercle vide, soit le point d’arrêt est désactivé ou avertissement s’est produite lors de la tentative de définir le point d’arrêt. Pour déterminer la différence, pointez sur le point d’arrêt et s’il existe un avertissement.

Les deux sections suivantes décrivent des avertissements importants et comment les résoudre. 

### <a name="no-symbols-have-been-loaded-for-this-document"></a>« Aucun symbole n’ont été chargés pour ce document » 

Accédez à la **Modules** fenêtre (**déboguer** > **Windows** > **Modules**) et vérifiez si votre module est chargé.  
* Si votre module est chargé, vérifiez le **état du symbole** colonne pour voir si des symboles ont été chargés. 
  * Si les symboles ne sont pas chargés, vérifiez l’état du symbole pour diagnostiquer le problème. Dans le menu contextuel sur un module dans le **Modules** fenêtre, cliquez sur **informations de chargement des symboles...**  pour voir où le débogueur effectue la recherche et essayez de charger les symboles. Pour plus d’informations sur le chargement de symboles, consultez [spécifier de symboles (.pdb) et les fichiers sources](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).  
  * Si les symboles sont chargés, cela signifie que le fichier PDB ne contient pas d’informations sur vos fichiers sources. Voici quelques causes possibles : 
    * Si vos fichiers sources ont été ajoutés récemment, vérifiez qu’une version à jour du module est chargée.  
    * Il est possible de créer des fichiers PDF supprimés à l’aide de la **/PDBSTRIPPED** option de l’éditeur de liens. Fichiers PDF supprimés ne contiennent pas les informations du fichier source. Confirmez que vous utilisez intégral PDB et pas un fichier PDB supprimé.  
    * Le fichier PDB est partiellement endommagé. Essayez de supprimer le fichier et effectuer un nettoyage de build du module pour vérifier si cela résout le problème. 

* Si votre module n’est pas chargé, vérifiez la commande suivante pour rechercher la cause : 
  * Vérifiez que vous déboguez le processus adéquat. 
  * Vérifiez que vous déboguez le bon type de code. Vous pouvez déterminer le type de code, le débogueur est configuré pour déboguer dans le **processus** fenêtre (**déboguer** > **Windows**  >  **Processus**). Par exemple, si vous essayez de déboguer du code c#, vérifiez que le débogueur est configuré pour le type approprié de .NET Framework (gérés, par exemple, (v4\*) ou managé (v2\*/v3\*) ou managé (CoreCLR)). 

### <a name="-the-current-source-code-is-different-from-the-version-built-into"></a>"… le code source actuel est différent de la version intégrée... » 

Si un fichier source a été modifié et que la source ne correspond plus au code que vous déboguez, le débogueur ne définit pas les points d’arrêt dans le code par défaut. En règle générale, ce problème se produit lorsqu’un fichier source est modifié, mais le code source n’a pas été reconstruit. Pour résoudre ce problème, régénérez le projet. Si le système de génération pense que le projet est déjà à jour même si elle n’est pas, vous pouvez forcer le système de projet à reconstruire en enregistrer de nouveau le fichier source ou par un nettoyage du projet sortie avant la génération de la génération. 

Dans de rares scénarios, vous souhaiterez déboguer sans code source correspondant. Cela peut conduire à une expérience de débogage très déroutant, assurez-vous qu’il s’agit comment vous souhaitez continuer.  

Pour désactiver ces vérifications de sécurité, effectuez l’une des opérations suivantes : 
* Pour modifier un point d’arrêt, placez le curseur sur l’icône de point d’arrêt dans l’éditeur, puis cliquez sur l’icône Paramètres (engrenage). Une fenêtre d’aperçu est ajoutée à l’éditeur. En haut de la fenêtre d’aperçu, il existe un lien hypertexte qui indique l’emplacement du point d’arrêt. Cliquez sur le lien hypertexte pour autoriser la modification de l’emplacement du point d’arrêt et vérifier **permettre que le code source soit différent de l’original**.
* Pour modifier ce paramètre pour les points d’arrêt, accédez à **déboguer** > **Options et paramètres**. Dans la page **Débogage/Général** , désactivez l’option **Les fichiers sources doivent correspondre exactement à la version d’origine** . Veillez à réactiver cette option lorsque vous avez terminé le débogage. 

## <a name="the-breakpoint-was-successfully-set-no-warning-but-didnt-hit"></a>Le point d’arrêt a été correctement définie (aucun avertissement), mais n’a pas été atteint 

Cette section fournit des informations pour résoudre les problèmes lorsque le débogueur n’affiche pas les avertissements : le point d’arrêt est un cercle rouge uni pendant le débogage activement, mais le point d’arrêt n’est pas en cours d’accès. 

Voici quelques points à vérifier : 
1. Si votre code s’exécute dans un processus plus d’un ou plusieurs ordinateurs, assurez-vous que vous déboguez le processus adéquat ou l’ordinateur.  
2. Assurez-vous que votre code s’exécute. Un moyen facile de ce test consiste à ajouter un appel à `System.Diagnostics.Debugger.Break` (C# /Visual Basic) ou `__debugbreak` (C++) à la ligne de code où vous essayez de définir le point d’arrêt et puis régénérez votre projet. 
3. Si vous déboguez du code optimisé, assurez-vous que la fonction où votre point d’arrêt est défini n’est pas en cours inline dans une autre fonction. Le `Debugger.Break` test décrit dans la vérification de la précédente peut utiliser pour ce test ainsi. 

## <a name="i-deleted-a-breakpoint-but-i-continue-to-hit-it-when-i-start-debugging-again"></a>J’ai supprimé un point d’arrêt, mais je continue de l’atteindre quand je relance le débogage 

Si vous avez supprimé un point d’arrêt pendant le débogage, vous pouvez atteindre le point d’arrêt de la prochaine fois que vous démarrez le débogage. Pour cesser d’atteindre ce point d’arrêt, assurez-vous que toutes les instances du point d’arrêt sont supprimées de la fenêtre **Points d’arrêt** .  
