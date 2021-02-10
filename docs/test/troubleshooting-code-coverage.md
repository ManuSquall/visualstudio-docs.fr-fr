---
title: Dépannage de la couverture du code
description: Découvrez comment résoudre les messages de résultats vides erronés quand vous vous attendez à ce que Visual Studio collecte des données pour les assemblys natifs et managés.
ms.custom: SEO-VS-2020
ms.date: 03/31/2020
ms.topic: troubleshooting
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: d99dcc3a141bc3734c5c356601d0e1e7474f06a7
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99967967"
---
# <a name="troubleshoot-code-coverage"></a>Résoudre les problèmes liés à la couverture du code

L’outil d’analyse de couverture du code dans Visual Studio collecte des données pour les assemblys natifs et managés (fichiers *. dll* ou *. exe* ). Toutefois, dans certains cas, la fenêtre résultats de la **couverture du code** affiche une erreur semblable à « les résultats vides ont été générés :... ». Il existe plusieurs raisons pour lesquelles vous pouvez obtenir des résultats vides. Cet article vous aide à résoudre ces problèmes.

## <a name="what-you-should-see"></a>Ce qui suit doit s'afficher

Si vous choisissez une commande **analyser la couverture du code** dans le menu **test** et si la génération et les tests s’exécutent correctement, vous devez voir une liste de résultats dans la fenêtre de couverture du **code** . Vous devrez peut-être développer les éléments pour afficher les détails.

::: moniker range=">=vs-2019"
![Résultats de la couverture du code avec coloration](../test/media/vs-2019/codecoverage1.png)
::: moniker-end
::: moniker range="vs-2017"
![Résultats de la couverture du code avec coloration](../test/media/codecoverage1.png)
::: moniker-end

Pour plus d’informations, consultez [Utiliser la couverture du code pour déterminer la quantité de code testé](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md).

## <a name="possible-reasons-for-seeing-no-results-or-old-results"></a>Raisons pouvant justifier qu'aucun résultat ne s'affichent, ou que seuls des résultats anciens s'affichent

### <a name="do-you-have-the-right-edition-of-visual-studio"></a>Utilisez-vous l'édition appropriée de Visual Studio ?

Vous avez besoin de Visual Studio Enterprise.

### <a name="no-tests-were-executed"></a>Aucun test n'a été exécuté

Analyse &mdash; vérifiez votre fenêtre de sortie. Dans la liste déroulante **Afficher la sortie à partir de**, choisissez **Tests**. Vérifiez si des avertissements ou des erreurs sont enregistrés.

Explication &mdash; l’analyse de la couverture du code est effectuée pendant l’exécution de tests. Elle inclut uniquement les assemblys chargés en mémoire lorsque les tests s'exécutent. Si aucun des tests n’est exécuté, la couverture du code n’a rien a signaler.

Résolution &mdash; dans l’Explorateur de tests, choisissez **Exécuter tout** pour vérifier que l’exécution des tests a réussi. Corrigez toutes les erreurs avant d’utiliser **Analyser la couverture du code**.

### <a name="youre-looking-at-a-previous-result"></a>Vous consultez un résultat antérieur

Quand vous modifiez et que vous réexécutez vos tests, le résultat d’une couverture du code antérieure peut être toujours visible, notamment la coloration du code de cette exécution antérieure.

1. Exécutez **analyser la couverture du code**.

2. Assurez-vous que vous avez sélectionné le jeu de résultats le plus récent dans la fenêtre résultats de la **couverture du code** .

### <a name="pdb-symbol-files-are-unavailable"></a>Les fichiers .pdb (symbole) ne sont pas disponibles

Analyse &mdash; Ouvrez le dossier cible de compilation (généralement *bin\Debug*) et vérifiez que pour chaque assembly, il existe un fichier *. pdb* dans le même répertoire que le fichier *. dll* ou *. exe* .

Explication &mdash; le moteur de couverture du code requiert que le fichier *. pdb* associé à chaque assembly soit accessible pendant la série de tests. S’il n’existe aucun fichier *. pdb* pour un assembly particulier, l’assembly n’est pas analysé.

Le fichier *. pdb* doit être généré à partir de la même build que les fichiers. *dll* ou *. exe* .

Résolution Assurez-vous &mdash; que vos paramètres de génération génèrent le fichier *. pdb* . Si les fichiers *. pdb* ne sont pas mis à jour lors de la génération du projet, ouvrez les propriétés du projet, sélectionnez la page **générer** , choisissez **avancé**, puis inspecter les **informations de débogage**.

Pour les projets C++, vérifiez que les fichiers. pdb générés contiennent des informations de débogage complètes. Ouvrez les propriétés du projet et vérifiez que le débogage de l' **éditeur de liens**  >    >  **générer** des informations de débogage est défini pour **générer des informations de débogage optimisées pour le partage et la publication (/Debug : Full)**.

Si les fichiers *. pdb* et *. dll* ou *. exe* se trouvent dans des emplacements différents, copiez le fichier *. pdb* dans le même répertoire. Il est également possible de configurer le moteur de couverture du code pour rechercher des fichiers *. pdb* dans un autre emplacement. Pour plus d’informations, consultez [Personnaliser l’analyse de la couverture du code](../test/customizing-code-coverage-analysis.md).

### <a name="use-an-instrumented-or-optimized-binary"></a>Utiliser un fichier binaire instrumenté ou optimisé

&mdash;L’analyse détermine si le fichier binaire a subi une forme d’optimisation avancée telle que l’optimisation guidée par profil, ou s’il a été instrumenté par un outil de profilage tel que *vsinstr.exe* ou *vsperfmon.exe*.

Explication &mdash; si un assembly a déjà été instrumenté ou optimisé par un autre outil de profilage, l’assembly est omis de l’analyse de la couverture du code. L’analyse de la couverture du code ne peut pas être exécutée sur ces assemblys.

Résolution &mdash; désactivez l’optimisation et utilisez une nouvelle build.

### <a name="code-is-not-managed-net-or-native-c-code"></a>Le code n'est pas managé (.NET) ou le code est natif (C++)

Analyse &mdash; vérifiez que vous exécutez des tests sur du code managé ou du code C++.

Explication &mdash; l’analyse de la couverture du code dans Visual Studio est disponible seulement sur du code managé et sur du code natif (C++). Si vous utilisez des outils tiers, tout ou partie du code peut s’exécuter sur une autre plateforme.

Résolution &mdash; Pas de résolution disponible.

### <a name="assembly-has-been-installed-by-ngen"></a>L'assembly a été installé par NGen

Analyse &mdash; vérifiez que l’assembly n’est pas chargé à partir du cache des images natives.

Explication &mdash; pour des raisons de performances, les assemblys d’image natives ne sont pas analysés. Pour plus d’informations, consultez [Ngen.exe (Native Image Generator)](/dotnet/framework/tools/ngen-exe-native-image-generator).

Résolution &mdash; utilisez une version MSIL de l’assembly. Ne le traitez pas avec NGen.

### <a name="custom-runsettings-file-with-bad-syntax"></a>Fichier personnalisé .runsettings comportant une syntaxe incorrecte

Analyse &mdash; si vous utilisez un fichier *.runsettings* personnalisé, il peut contenir une erreur de syntaxe. La couverture du code n’est pas exécutée, et la fenêtre de couverture du code ne s’ouvre pas à l’issue de l’exécution du test ou elle affiche des résultats anciens.

Explication &mdash; vous pouvez exécuter vos tests unitaires avec un fichier *. RunSettings* personnalisé pour configurer les options de couverture du code. Les options vous permettent d'inclure ou d'exclure des fichiers. Pour plus d’informations, consultez [Personnaliser l’analyse de la couverture du code](../test/customizing-code-coverage-analysis.md).

Résolution &mdash; il existe deux types d’erreurs possibles :

- **Erreur XML**

     Ouvrez le fichier *. RunSettings* dans l’éditeur XML de Visual Studio. Recherchez les indications des erreurs.

- **Erreur d’expressions régulières**

  Chaque chaîne du fichier est une expression régulière. Vérifiez la présence d’erreurs dans chaque expression régulière. Recherchez en particulier :

  - Parenthèses non appariées (…) ou parenthèses sans séquence d’échappement \\(...\\). Si vous souhaitez faire correspondre une parenthèse dans la chaîne de recherche, vous devez l'échapper. Par exemple, pour faire correspondre à une fonction, utilisez : `.*MyFunction\(double\)`

  - Astérisque ou plus au début d'une expression. Pour faire correspondre à n'importe quelle chaîne de caractères, utilisez un point suivi d'un astérisque : `.*`

### <a name="custom-runsettings-file-with-incorrect-exclusions"></a>Fichier .runsettings personnalisé avec des exclusions non valides

Analyse &mdash; si vous utilisez un fichier *.runsettings* personnalisé, vérifiez qu’il inclut votre assembly.

Explication &mdash; vous pouvez exécuter vos tests unitaires avec un fichier *. RunSettings* personnalisé pour configurer les options de couverture du code. Les options vous permettent d'inclure ou d'exclure des fichiers. Pour plus d’informations, consultez [Personnaliser l’analyse de la couverture du code](../test/customizing-code-coverage-analysis.md).

Résolution &mdash; supprimez tous les `Include` nœuds du fichier *. RunSettings* , puis supprimez tous les `Exclude` nœuds. Si cela résout le problème, remettez-les en étapes.

Assurez-vous que le nœud DataCollectors spécifie la couverture du code. Comparez-le à l’exemple dans [Personnaliser l’analyse de la couverture du code](../test/customizing-code-coverage-analysis.md).

## <a name="some-code-is-always-shown-as-not-covered"></a>Du code est toujours affiché comme non couvert

### <a name="initialization-code-in-native-dlls-is-executed-before-instrumentation"></a>Le code d'initialisation dans les DLL natives est exécuté avant instrumentation

Analyse &mdash; dans le code natif lié statiquement, une partie de la fonction d’initialisation **DllMain** et le code qu’elle appelle est parfois affiché comme non couvert, même si le code a été exécuté.

Explication &mdash; l’outil de couverture du code fonctionne en insérant une instrumentation dans un assembly juste avant que l’application commence à s’exécuter. Dans n’importe quel assembly chargé au préalable, le code d’initialisation dans **DllMain** s’exécute dès le chargement de l’assembly, et avant l’exécution de l’application. Ce code apparaît comme étant non couvert, ce qui s’applique généralement aux assemblys chargés statiquement.

Résolution &mdash; aucune.

## <a name="see-also"></a>Voir aussi

- [Utiliser la couverture du code pour déterminer la quantité de code testé](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md)
