---
title: Résolution des problèmes liés à la couverture du code | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: troubleshooting
ms.assetid: 26de91b8-45e3-4976-a20e-a3bd1942ddcb
caps.latest.revision: 13
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c2bf21286143b2b9543c834f00ed31ddaa4cef63
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72660371"
---
# <a name="troubleshooting-code-coverage"></a>Dépannage de la couverture du code
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

L'outil d'analyse de couverture du code dans Visual Studio collecte des données pour le code natif et les assemblys managés (fichiers .dll ou .exe). Toutefois, dans certains cas, la fenêtre résultats de la couverture du code affiche une erreur semblable à « les résultats vides ont été générés :... ». Cela peut se produire pour plusieurs raisons. Cette rubrique est conçue pour aider à résoudre ces problèmes.

## <a name="what-you-should-see"></a>Ce que vous devriez voir
 Si vous choisissez une commande **Analyser la couverture du code** dans le menu Test, et que la génération et les tests s’exécutent correctement, une liste de résultats doit s’afficher dans la fenêtre Couverture du code. Vous devrez peut-être développer les éléments pour afficher les détails.

 ![Résultats de couverture du code avec coloration](../test/media/codecoverage1.png "CodeCoverage1")

 Pour plus d’informations, consultez [Utilisation de la couverture du code pour déterminer la quantité de code testé](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md).

## <a name="possible-reasons-for-seeing-no-results-or-old-results"></a>Raisons pouvant justifier qu'aucun résultat ne s'affichent, ou que seuls des résultats anciens s'affichent

### <a name="do-you-have-the-right-edition-of-visual-studio"></a>Utilisez-vous l'édition appropriée de Visual Studio ?
 Vous avez besoin de Visual Studio Enterprise.

### <a name="no-tests-were-executed"></a>Aucun test n'a été exécuté
 Analyse Vérifiez votre fenêtre de sortie. Dans la liste déroulante **Afficher la sortie à partir de**, choisissez **Tests**. Vérifiez si des avertissements ou des erreurs sont enregistrés.

 Explication l’analyse de la couverture du code est effectuée pendant l’exécution des tests. Elle inclut uniquement les assemblys chargés en mémoire lorsque les tests s'exécutent. Si aucun des tests n'est exécuté, la couverture du code n'a rien a signaler.

 Résolution dans l’Explorateur de tests, choisissez **exécuter tout** pour vérifier que les tests s’exécutent correctement. Corrigez toutes les erreurs avant d’utiliser **Analyser la couverture du code**.

### <a name="youre-looking-at-a-previous-result"></a>Vous consultez un résultat antérieur
 Lorsque vous modifiez et exécutez à nouveau vos tests, un résultat de couverture du code antérieur peut être visible, y compris la coloration du code de cette exécution antérieure.

1. Exécutez Analyser la couverture du code.

2. Vérifiez que vous avez sélectionné le jeu de résultats le plus récent dans la fenêtre Résultats de la couverture du code.

### <a name="pdb-symbol-files-are-unavailable"></a>Les fichiers .pdb (symbole) ne sont pas disponibles
 Analyse Ouvrez le dossier cible de compilation (généralement bin\Debug) et vérifiez que, pour chaque assembly, il existe un fichier. pdb dans le même répertoire que le fichier. dll ou. exe.

 Explication le moteur de couverture du code requiert que le fichier. pdb associé à chaque assembly soit accessible pendant la série de tests. S'il n'existe aucun fichier .pdb pour un assembly particulier, il ne sera pas analysé.

 Le fichier .pdb doit être généré à partir de la même version que les fichiers .dll ou .exe.

 Résolution Assurez-vous que vos paramètres de génération génèrent le fichier. pdb. Si les fichiers .pdb ne sont pas mis à jour quand le projet est généré, ouvrez les propriétés du projet, sélectionnez la page **Générer**, choisissez **Avancé** et examinez **Informations de débogage**.

 Si les fichiers .pdb et .dll ou .exe sont dans des endroits différents, copiez le fichier .pdb dans le même dossier. Il est également possible de configurer le moteur de couverture du code pour rechercher les fichiers .pdb dans un autre emplacement. Pour plus d’informations, consultez [Personnalisation de l’analyse de couverture du code](../test/customizing-code-coverage-analysis.md).

### <a name="using-an-instrumented-or-optimized-binary"></a>À l'aide d'un fichier binaire instrumenté ou optimisé
 L’analyse détermine si le fichier binaire a subi une forme d’optimisation avancée telle que l’optimisation guidée par profil, ou s’il a été instrumenté par un outil de profilage tel que VSInstr. exe ou VSPerfMon. exe.

 Explication si un assembly a déjà été instrumenté ou optimisé par un autre outil de profilage, l’assembly est omis de l’analyse de couverture du code.

 L'analyse de la couverture du code ne peut pas être exécutée sur ce type d'assemblys.

 Résolution : désactivez l’optimisation et utilisez une nouvelle Build.

### <a name="code-is-not-managed-net-or-native-c-code"></a>Le code n'est pas managé (.NET) ou le code est natif (C++)
 Analyse Vérifiez que vous exécutez des tests sur le code géré C++ ou.

 Explication l’analyse de couverture du code dans Visual Studio est uniquement disponible sur duC++code managé et natif (). Si vous utilisez des outils tiers, une partie ou la totalité du code peut s'exécuter sur une plateforme différente.

 Résolution aucun disponible.

### <a name="assembly-has-been-installed-by-ngen"></a>L'assembly a été installé par NGen
 Analyse Vérifiez que l’assembly n’est pas chargé à partir du cache des images natives.

 Explication pour des raisons de performances, les assemblys d’images natives ne sont pas analysés. Pour plus d’informations, consultez [Ngen.exe (Native Image Generator)](https://msdn.microsoft.com/library/44bf97aa-a9a4-4eba-9a0d-cfaa6fc53a66).

 La résolution utilise une version MSIL de l’assembly. Ne pas le traiter avec NGen.

### <a name="custom-runsettings-file-with-bad-syntax"></a>Fichier personnalisé .runsettings comportant une syntaxe incorrecte
 Analyse si vous utilisez un fichier. RunSettings personnalisé, il peut contenir une erreur de syntaxe.

 Cela empêche l'exécution de la couverture du code. Soit la fenêtre de couverture du code ne s'ouvre pas à l'issue de l'exécution du test, soit elle affiche d'anciens résultats.

 Explication vous pouvez exécuter vos tests unitaires avec un fichier. RunSettings personnalisé pour configurer les options de couverture du code. Les options vous permettent d'inclure ou d'exclure des fichiers. Pour plus d’informations, consultez [Personnalisation de l’analyse de couverture du code](../test/customizing-code-coverage-analysis.md).

 Résolution il existe deux types d’erreurs possibles :

- **Erreur XML**

     Ouvrez le fichier .runsettings dans l'éditeur XML de Visual Studio. Recherchez les indications des erreurs.

- **Erreur d’expressions régulières**

  Chaque chaîne du fichier est une expression régulière. Vérifiez la présence d’erreurs pour chaque expression régulière. Recherchez en particulier :

  - Parenthèses non appariées (…) ou parenthèses sans séquence d’échappement \\(...\\). Si vous souhaitez faire correspondre une parenthèse dans la chaîne de recherche, vous devez l'échapper. Par exemple, pour faire correspondre à une fonction, utilisez : `.*MyFunction\(double\)`

  - Astérisque ou plus au début d'une expression. Pour faire correspondre à n'importe quelle chaîne de caractères, utilisez un point suivi d'un astérisque : `.*`

### <a name="custom-runsettings-file-with-incorrect-exclusions"></a>Fichier .runsettings personnalisé avec des exclusions non valides
 Analyse si vous utilisez un fichier. RunSettings personnalisé, assurez-vous qu’il comprend votre assembly.

 Explication vous pouvez exécuter vos tests unitaires avec un fichier. RunSettings personnalisé pour configurer les options de couverture du code. Les options vous permettent d'inclure ou d'exclure des fichiers. Pour plus d’informations, consultez [Personnalisation de l’analyse de couverture du code](../test/customizing-code-coverage-analysis.md).

 Résolution supprimez tous les nœuds `Include` du fichier. RunSettings, puis supprimez tous les nœuds de `Exclude`. Si cela résout le problème, remettez-les en étapes.

 Assurez-vous que le nœud DataCollectors spécifie la couverture du code. Comparez-le avec l’exemple dans [Personnalisation de l’analyse de la couverture du code](../test/customizing-code-coverage-analysis.md).

## <a name="some-code-is-always-shown-as-not-covered"></a>Du code est toujours affiché comme non couvert

### <a name="initialization-code-in-native-dlls-is-executed-before-instrumentation"></a>Le code d'initialisation dans les DLL natives est exécuté avant instrumentation
 L’analyse dans le code natif lié de manière statique, qui fait partie de la fonction d’initialisation **DllMain** et du code qu’il appelle, est parfois indiquée comme non couverte, même si le code a été exécuté.

 Explication l’outil de couverture du code fonctionne en insérant l’instrumentation dans un assembly juste avant que l’application commence à s’exécuter. Dans n’importe quel assembly chargé au préalable, le code d’initialisation dans **DllMain** s’exécute dès le chargement de l’assembly, et avant l’exécution de l’application. Ce code apparaîtra comme étant non couvert.

 En général, cela s'applique aux assemblys chargés statiquement.

 Résolution None.

## <a name="see-also"></a>Voir aussi
 [Utilisation de la couverture du code pour déterminer la quantité de code testé](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md)
