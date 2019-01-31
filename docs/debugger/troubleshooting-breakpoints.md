---
title: Résoudre les problèmes de points d’arrêt dans le débogueur | Microsoft Docs
ms.custom: seodec18
ms.date: 01/23/2018
ms.topic: troubleshooting
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 23ff00cea9bda6216a87bfd64b8c2c72ea5c3c2a
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54987789"
---
# <a name="troubleshoot-breakpoints-in-the-visual-studio-debugger"></a>Résoudre les problèmes de points d’arrêt dans le débogueur Visual Studio

## <a name="breakpoint-warnings"></a>Avertissements de point d’arrêt

Lors du débogage, un point d’arrêt a deux états visuels possible : un cercle rouge plein et des creux (remplie de blanc) cercle. Si le débogueur est en mesure de définir correctement un point d’arrêt dans le processus cible, il reste un cercle rouge plein. Si le point d’arrêt est un cercle vide, le point d’arrêt est désactivé ou avertissement s’est produite lors de la tentative définir le point d’arrêt. Pour déterminer la différence, placez le curseur sur le point d’arrêt et voir si un avertissement s’affiche.

Les deux sections suivantes décrivent les avertissements importants et comment les résoudre. 

### <a name="no-symbols-have-been-loaded-for-this-document"></a>« Aucun symbole n’a été chargé pour ce document » 

Accédez à la **Modules** fenêtre (**déboguer** > **Windows** > **Modules**) et vérifiez si votre module chargé.  
* Si votre module est chargé, vérifiez le **état du symbole** colonne pour voir si les symboles ont été chargés. 
  * Si les symboles ne sont pas chargés, vérifiez l’état du symbole pour diagnostiquer le problème. Dans le menu contextuel sur un module dans le **Modules** fenêtre, cliquez sur **informations de chargement des symboles...**  pour voir où le débogueur est consulté pour tenter de charger des symboles. Pour plus d’informations sur le chargement de symboles, consultez [spécifier le symbole (.pdb) et les fichiers sources](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).  
  * Si les symboles sont chargés, le fichier PDB ne contient pas d’informations sur vos fichiers sources. Voici quelques causes possibles : 
    * Si vos fichiers sources ont été ajoutées récemment, vérifiez qu’une version à jour du module est chargée.  
    * Il est possible de créer des fichiers PDF supprimés à l’aide de la **/PDBSTRIPPED** option de l’éditeur de liens. Fichiers PDF supprimés ne contiennent pas les informations du fichier source. Vérifiez que vous travaillez avec un intégral PDB et pas sur un fichier PDB supprimé.  
    * Le fichier PDB est partiellement endommagé. Supprimez le fichier et effectuer une génération complète du module pour essayer de résoudre le problème. 

* Si votre module n’est pas chargé, vérifiez la commande suivante pour rechercher la cause : 
  * Vérifiez que vous déboguez le processus correct. 
  * Vérifiez que vous déboguez le bon type de code. Vous pouvez trouver le type de code, le débogueur est configuré pour déboguer dans le **processus** fenêtre (**déboguer** > **Windows**  >  **Processus**). Par exemple, si vous essayez de déboguer C# de code, vérifiez que votre débogueur est configuré pour le type de .NET Framework approprié (par exemple, géré (v4\*) et géré (v2\*/v3\*) et géré (CoreCLR)) . 

### <a name="-the-current-source-code-is-different-from-the-version-built-into"></a>"… le code source en cours est différent de la version intégrée... » 

Si un fichier source a changé et que la source ne correspond plus au code que vous déboguez, le débogueur ne définit pas les points d’arrêt dans le code par défaut. En règle générale, ce problème se produit lorsqu’un fichier source est modifié, mais le code source n’a pas été reconstruit. Pour résoudre ce problème, régénérez le projet. Si le système de génération considère que le projet est déjà à jour même si elle n’est pas, vous pouvez forcer le système de projet de reconstruction en enregistrer de nouveau le fichier source ou en effaçant du projet sortie avant la génération de la génération. 

Dans rares cas, vous souhaiterez déboguer sans code source correspondant. Débogage sans correspondance de code source peut entraîner une confusion débogage expérience, veillez donc qu’il s’agit de façon dont vous souhaitez continuer.  

Pour désactiver ces vérifications de sécurité, effectuez l’une des opérations suivantes : 
* Pour modifier un point d’arrêt, placez le curseur sur l’icône de point d’arrêt dans l’éditeur, puis cliquez sur l’icône des paramètres (engrenage). Une fenêtre d’aperçu est ajoutée à l’éditeur. En haut de la fenêtre d’aperçu, il existe un lien hypertexte qui indique l’emplacement du point d’arrêt. Cliquez sur le lien hypertexte pour autoriser la modification de l’emplacement du point d’arrêt et vérifier **permettent au code source soit différent de celui d’origine**.
* Pour modifier ce paramètre pour tous les points d’arrêt, accédez à **déboguer** > **Options et paramètres**. Dans la page **Débogage/Général** , désactivez l’option **Les fichiers sources doivent correspondre exactement à la version d’origine** . N’oubliez pas de réactiver cette option lorsque vous avez terminé le débogage. 

## <a name="the-breakpoint-was-successfully-set-no-warning-but-didnt-hit"></a>Le point d’arrêt a été correctement définie (aucun avertissement), mais n’a pas d’accès 

Cette section fournit des informations pour résoudre les problèmes lorsque le débogueur ne s’affiche pas les avertissements : le point d’arrêt est un cercle rouge plein pendant le débogage activement, mais le point d’arrêt n’est pas en cours d’accès. 

Voici quelques points à vérifier : 
1. Si votre code s’exécute dans plusieurs processus ou de plusieurs ordinateurs, assurez-vous que vous déboguez le processus correct ou l’ordinateur.  
2. Vérifiez que votre code s’exécute. Pour vérifier que votre code s’exécute, ajoutez un appel à `System.Diagnostics.Debugger.Break` (C#/VB) ou `__debugbreak` (C++) à la ligne de code où vous essayez de définir le point d’arrêt et puis régénérez votre projet. 
3. Si vous déboguez du code optimisé, assurez-vous que la fonction où votre point d’arrêt est défini n’est pas en cours d’inline dans une autre fonction. Le `Debugger.Break` test décrit dans la vérification précédente peut travailler pour tester également ce problème. 

## <a name="i-deleted-a-breakpoint-but-i-continue-to-hit-it-when-i-start-debugging-again"></a>J’ai supprimé un point d’arrêt, mais je continue de l’atteindre quand je relance le débogage 

Si vous avez supprimé un point d’arrêt pendant le débogage, vous peut-être atteint le point d’arrêt de la prochaine fois que vous démarrez le débogage. Pour cesser d’atteindre ce point d’arrêt, assurez-vous que toutes les instances du point d’arrêt sont supprimées de la fenêtre **Points d’arrêt** .  
