---
title: Résoudre les problèmes de points d’arrêt dans le débogueur | Microsoft Docs
description: Si un point d’arrêt est désactivé ou n’a pas pu être défini, il est affiché sous la forme d’un cercle vide. Consultez cette page pour obtenir des informations sur les problèmes qui peuvent se produire lors de la définition de points d’arrêt.
ms.custom: SEO-VS-2020
ms.date: 01/23/2018
ms.topic: troubleshooting
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 0801a687529b5e0f8cdf34030460f0b5fe45bc91
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112386382"
---
# <a name="troubleshoot-breakpoints-in-the-visual-studio-debugger"></a>Résoudre les problèmes de points d’arrêt dans le débogueur Visual Studio

## <a name="breakpoint-warnings"></a>Avertissements de point d’arrêt

Lors du débogage, un point d’arrêt a deux États visuels possibles : un cercle rouge plein et un cercle creux (blanc rempli). Si le débogueur peut définir correctement un point d’arrêt dans le processus cible, il reste un cercle rouge plein. Si le point d’arrêt est un cercle creux, le point d’arrêt est désactivé ou un avertissement s’est produit lors de la tentative de définition du point d’arrêt. Pour déterminer la différence, pointez sur le point d’arrêt et vérifiez s’il y a un avertissement.

Les deux sections suivantes décrivent les avertissements importants et comment les corriger.

### <a name="no-symbols-have-been-loaded-for-this-document"></a>« Aucun symbole n’a été chargé pour ce document »

Accédez à la fenêtre **modules** (**Déboguer** les  >    >  **modules** Windows) et vérifiez si votre module est chargé.
* Si votre module est chargé, consultez la colonne **État du symbole** pour voir si les symboles ont été chargés.
  * Si les symboles ne sont pas chargés, vérifiez l’état du symbole pour diagnostiquer le problème. Dans le menu contextuel d’un module de la fenêtre **modules** , cliquez sur informations sur le **chargement des symboles...** pour voir où le débogueur a essayé de charger les symboles. Pour plus d’informations sur le chargement de symboles, consultez [spécifier les fichiers de symboles (. pdb) et les fichiers sources](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).
  * Si les symboles sont chargés, le fichier PDB ne contient pas d’informations sur vos fichiers sources. Voici quelques causes possibles :
    * Si vos fichiers sources ont été ajoutés récemment, vérifiez qu’une version à jour du module est en cours de chargement.
    * Il est possible de créer des fichiers PDB supprimés à l’aide de l’option de l’éditeur de liens **/PDBSTRIPPED** . Les fichiers PDB supprimés ne contiennent pas d’informations sur le fichier source. Vérifiez que vous travaillez avec un fichier PDB complet et non un fichier PDB supprimé.
    * Le fichier PDB est partiellement endommagé. Supprimez le fichier et effectuez une génération propre du module pour tenter de résoudre le problème.

* Si votre module n’est pas chargé, vérifiez les éléments suivants pour trouver la cause :
  * Vérifiez que vous déboguez le processus correct.
  * Vérifiez que vous déboguez le type de code approprié. Vous pouvez déterminer le type de code que le débogueur est configuré pour déboguer dans la fenêtre **processus** (**Déboguer** les  >    >  **processus** Windows). Par exemple, si vous essayez de déboguer du code C#, vérifiez que votre débogueur est configuré pour le type et la version appropriés de .NET (par exemple, managé (v4 \* ) et managé (v2 \* /v3 \* ) par rapport à managé (CoreCLR)).

### <a name="-the-current-source-code-is-different-from-the-version-built-into"></a>"… le code source actuel est différent de la version intégrée à...»

Si un fichier source a été modifié et que la source ne correspond plus au code que vous déboguez, le débogueur ne définit pas les points d’arrêt dans le code par défaut. Normalement, ce problème se produit lorsqu’un fichier source est modifié, mais que le code source n’a pas été reconstruit. Pour résoudre ce problème, régénérez le projet. Si le système de génération estime que le projet est déjà à jour, même si ce n’est pas le cas, vous pouvez forcer le système de projet à effectuer une régénération en enregistrant à nouveau le fichier source ou en nettoyant la sortie de génération du projet avant la génération.

Dans de rares scénarios, vous souhaiterez peut-être déboguer sans avoir le code source correspondant. Le débogage sans code source correspondant peut aboutir à une expérience de débogage confuse. Assurez-vous que c’est bien ce que vous voulez faire.

Pour désactiver ces vérifications de sécurité, effectuez l’une des opérations suivantes :
* Pour modifier un point d’arrêt unique, pointez sur l’icône du point d’arrêt dans l’éditeur, puis cliquez sur l’icône Paramètres (engrenage). Une fenêtre d’aperçu est ajoutée à l’éditeur. En haut de la fenêtre d’aperçu, un lien hypertexte indique l’emplacement du point d’arrêt. Cliquez sur le lien hypertexte pour autoriser la modification de l’emplacement du point d’arrêt et cochez **la case permettre que le code source soit différent de celui d’origine**.
* Pour modifier ce paramètre pour tous les points d’arrêt, accédez à options de **débogage**  >  **et paramètres**. Dans la page **Débogage/Général** , désactivez l’option **Les fichiers sources doivent correspondre exactement à la version d’origine** . Veillez à réactiver cette option lorsque vous avez terminé le débogage.

## <a name="the-breakpoint-was-successfully-set-no-warning-but-didnt-hit"></a>Le point d’arrêt a été correctement défini (aucun avertissement), mais n’a pas été atteint

Cette section fournit des informations pour résoudre les problèmes lorsque le débogueur n’affiche aucun avertissement : le point d’arrêt est un cercle rouge plein lors du débogage activement, mais le point d’arrêt n’est pas atteint.

Voici quelques éléments à vérifier :
1. Si votre code s’exécute dans plusieurs processus ou sur plusieurs ordinateurs, assurez-vous que vous déboguez le processus ou l’ordinateur approprié.
2. Vérifiez que votre code est en cours d’exécution. Pour vérifier que votre code est en cours d’exécution, ajoutez un appel à `System.Diagnostics.Debugger.Break` (C#/VB) ou `__debugbreak` (C++) à la ligne de code où vous essayez de définir le point d’arrêt, puis régénérez votre projet.
3. Si vous déboguez du code optimisé, assurez-vous que la fonction dans laquelle le point d’arrêt est défini n’est pas insérée dans une autre fonction. Le `Debugger.Break` test décrit dans la vérification précédente peut également fonctionner pour tester ce problème.

## <a name="i-deleted-a-breakpoint-but-i-continue-to-hit-it-when-i-start-debugging-again"></a>J’ai supprimé un point d’arrêt, mais je continue de l’atteindre quand je relance le débogage

Si vous avez supprimé un point d’arrêt pendant le débogage, vous pouvez atteindre à nouveau le point d’arrêt la prochaine fois que vous démarrez le débogage. Pour cesser d’atteindre ce point d’arrêt, assurez-vous que toutes les instances du point d’arrêt sont supprimées de la fenêtre **Points d’arrêt** .
