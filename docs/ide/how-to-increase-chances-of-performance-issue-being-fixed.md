---
title: Comment pouvez-vous augmenter les chances d’un problème de performance
description: Informations supplémentaires et pratiques exemplaires pour soumettre des questions de performance dans Visual Studio
author: madskristensen
ms.author: madsk
ms.date: 11/19/2019
ms.topic: reference
ms.openlocfilehash: f5c83a145eb56dcb95c6e9a299c690ae960442c9
ms.sourcegitcommit: 4bcd6abb89feff1cf8251e3ded73fdc30b67e347
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/17/2020
ms.locfileid: "81615042"
---
# <a name="how-to-increase-the-chances-of-a-performance-issue-being-fixed"></a>Comment augmenter les chances de fixer un problème de performance

L’outil «[Report a problem](/visualstudio/ide/how-to-report-a-problem-with-visual-studio?view=vs-2019)» est largement utilisé par les utilisateurs de Visual Studio pour signaler une série de problèmes. L’équipe Visual Studio repère les tendances de l’accident et de la lenteur dans la rétroaction des utilisateurs et aborde les problèmes ayant un large nombre d’utilisateurs. Plus un billet de rétroaction spécifique est exploitable, plus il sera susceptible d’être diagnostiqué et résolu rapidement par l’équipe du produit. Ce document décrit les meilleures pratiques tout en signalant des problèmes d’accident ou de lenteur pour les rendre plus exploitables.

## <a name="general-best-practices"></a>Bonnes pratiques générales

Visual Studio est une grande plate-forme complexe qui prend en charge une multitude de langues, types de projets, plates-formes, et plus encore. La façon dont il fonctionne est une fonction des composants installés et actifs dans une session, les extensions installées, les paramètres Visual Studio, la configuration de la machine, et enfin la forme du code qui est en cours d’édition. Étant donné le nombre de variables, il est difficile de dire si le rapport de problème d’un utilisateur a le même problème sous-jacent qu’un rapport de problème d’un autre utilisateur, même si le symptôme visible est le même. Étant donné que, voici quelques pratiques exemplaires pour s’assurer que votre rapport de problème spécifique a plus de chances d’être diagnostiqué.

**Fournir un titre aussi spécifique que possible**

Recherchez des signatures distinctes pour le problème signalé et incluez autant que possible dans le titre. Si le titre est descriptif, il est moins probable que les utilisateurs ayant des problèmes sans rapport (mais même symptôme superficiel) voteront ou commentent votre billet, ce qui rend le diagnostic de *votre* problème plus difficile.

**En cas de doute, enregistrez un nouveau rapport de problème**

De nombreux problèmes peuvent ne pas avoir de signature distinctive ou des étapes à reproduire. Dans de tels cas, un nouveau rapport vaut mieux qu’un upvote ou un commentaire sur un autre rapport, qui signale un *symptôme*extérieur similaire . Selon le type de rapport, inclure des dossiers diagnostiques supplémentaires à votre rapport tel que décrit plus tard dans ce document.

**Pratiques exemplaires spécifiques aux problèmes**

Décrit ci-dessous sont des problèmes qui sont difficiles à diagnostiquer sans bons fichiers diagnostiques. Après avoir identifié le cas qui décrit le mieux votre problème, suivez les étapes de rétroaction spécifiques à ce cas.

-   [Crashs:](#crashes) Un accident se produit lorsque le processus (Visual Studio) se termine de façon inattendue.

-   [Insension :](#unresponsiveness) VS devient insensible pendant une période prolongée.

-   [Problèmes de lenteur :](#slowness-and-high-cpu-issues) Toute action spécifique en VS est plus lente que souhaitée

-   [CPU élevé:](#slowness-and-high-cpu-issues) Périodes prolongées d’utilisation inattendue élevée du processeur

-   [Questions hors-processus :](#out-of-process-issues) Un problème causé par un processus satellite Visual Studio

## <a name="crashes"></a>Crashes
Un accident se produit lorsque le processus (Visual Studio) se termine de façon inattendue.

**Crashs directement reproductibles**

Les plantages directement reproductibles sont des cas qui ont toutes les caractéristiques suivantes :

- Peut être observé en suivant un ensemble connu d’étapes

- Peut être observé sur plusieurs ordinateurs (si disponible)

- Peut être reproduit dans le code de l’échantillon ou dans un projet qui peut être lié ou fourni dans le cadre de la rétroaction (si les étapes impliquent l’ouverture d’un projet ou d’un document)

Pour ces questions, suivez les étapes de «[Comment signaler un problème](/visualstudio/ide/how-to-report-a-problem-with-visual-studio-2017)» et assurez-vous d’inclure :

-   Les étapes pour reproduire le problème

-   Un projet de répro autonome tel que décrit ci-dessus. Si la répro autonome n’est pas possible, alors s’il vous plaît inclure:

    -   La langue des projets\#ouverts (C, C, etc.)

    -   Le type de projet (Application Console, ASP.NET, etc.)


> [!NOTE]
> **Commentaires les plus précieux :** Pour ce cas, la rétroaction la plus précieuse est l’ensemble des étapes pour reproduire le problème avec le code source de l’échantillon.

**Accidents inconnus**

Si vous n’êtes pas sûr de ce qui cause vos accidents ou ils semblent aléatoires, alors vous pouvez capturer des décharges localement chaque fois que Visual Studio s’écrase et les joindre à des éléments de rétroaction distincts. Pour enregistrer les décharges localement lorsque Visual Studio s’écrase, exécutez les commandes suivantes dans une fenêtre de commande d’administrateur :

```
reg add "HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\Windows Error
Reporting\LocalDumps\devenv.exe"

reg add "HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\Windows Error
Reporting\LocalDumps\devenv.exe" /v DumpType /t REG_DWORD /d 2

reg add "HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\Windows Error
Reporting\LocalDumps\devenv.exe" /v DumpCount /t REG_DWORD /d 2

reg add "HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\Windows Error
Reporting\LocalDumps\devenv.exe" /v DumpFolder /t REG_SZ /d "C:\CrashDumps"
```

Personnalisez le nombre de décharges et le dossier de décharge, le cas échéant. Retrouvez plus d’informations sur ces paramètres [ici](/windows/win32/wer/collecting-user-mode-dumps).

> [!NOTE]
> Les décharges capturées à l’aide de Task Manager sont susceptibles d’être de la mauvaise mordant, ce qui les rend moins utilisables. La procédure décrite ci-dessus est la façon préférée de capturer un dépotoir de tas. Si vous voulez utiliser Task Manager, fermez celui qui est actuellement en cours d’exécution, lancez le gestionnaire de tâches 32bit (%windir%\\syswow64\\taskmgr.exe) et de recueillir un tas de décharge à partir de là.

> [!NOTE] 
> Chaque fichier de décharge produit par cette méthode sera jusqu’à 4 Go de taille. Assurez-vous de régler DumpFolder à un endroit avec un espace d’entraînement adéquat ou ajuster le DumpCount de manière appropriée.

Chaque fois que Visual Studio s’écrase, il va créer un fichier de décharge **devenv.exe.[ numéro].dmp** fichier dans l’emplacement configuré.

Ensuite, utilisez Visual Studio "Report a Problem..." Fonction. Il vous permettra d’attacher le dépotoir approprié.

1.  Localiser le fichier de décharge pour l’accident que vous signalez (recherchez un fichier avec le bon temps de création)

2.  Si possible, zip\*le fichier ( .zip) pour réduire sa taille avant de soumettre des commentaires

3.  Suivez les étapes de "[Comment signaler un problème](/visualstudio/ide/how-to-report-a-problem-with-visual-studio-2017)", et attachez le dépotoir de tas à un nouvel élément de rétroaction.

> [!NOTE] 
> **Commentaires les plus précieux :** Pour ce cas, la rétroaction la plus précieuse est la décharge de tas capturé au moment de l’accident.

## <a name="unresponsiveness"></a>Insension
VS devient insensible pendant une période prolongée.

**Unrésensivité directement reproductible**

Comme décrit dans la section correspondante sur les accidents, pour les problèmes qui peuvent être facilement reproduits, vus sur plusieurs machines et peuvent être démontrés dans un petit échantillon, les rapports de rétroaction les plus précieux sont ceux qui comprennent des étapes pour reproduire le problème, et inclure le code source de l’échantillon qui démontre le problème.

**Indétabilité inconnue**

Si un non-réponse se manifeste de façon imprévisible, sur la prochaine occurrence, lancez une nouvelle instance de Visual Studio et signalez un problème à partir de cette instance.
Dans [l’écran "Record",](/visualstudio/ide/how-to-report-a-problem-with-visual-studio?view=vs-2019#record-a-repro)assurez-vous de sélectionner la session Visual Studio qui ne répond pas.

Si l’instance Visual Studio qui ne répond pas a été lancée en mode Administrateur, alors la deuxième instance devrait également être lancée en mode Administrateur.

>[!NOTE] 
> **Commentaires les plus précieux :** Pour ce cas, la rétroaction la plus précieuse est le dépotoir de tas capturé au moment de l’unresponsivité.

## <a name="slowness-and-high-cpu-issues"></a>Slowness et High CPU Issues

Ce qui rend un problème de lenteur ou d’utilisation élevée de processeur le plus actionnable est une trace de performance capturée tandis que le fonctionnement lent ou l’événement de processeur élevé est en cours.

>[!NOTE] 
> Dans la mesure du possible, isolez chaque scénario dans un rapport de rétroaction distinct et spécifique.
Par exemple, si la dactylographie et la navigation sont lentes, suivez les étapes ci-dessous une fois par problème. Cela aide l’équipe du produit à isoler la cause de problèmes spécifiques.

Pour obtenir de meilleurs résultats dans la capture des performances, suivez ces étapes :

1.  Si vous n’êtes pas déjà en cours d’exécution, ayez une copie de Visual Studio ouverte où vous reproduirez le problème

    -   Faites tout mettre en place pour reproduire le problème. Par exemple, si vous avez besoin d’un projet particulier pour être chargé avec un fichier spécifique ouvert, alors assurez-vous que ces deux étapes sont terminées avant de procéder.

    -   Si vous ne signalez *pas* un problème spécifique au chargement d’une solution, essayez d’attendre 5-10 minutes (ou plus, selon la taille de la solution) après l’ouverture de la solution avant d’enregistrer la trace de performance. Le processus de chargement de la solution produit une grande quantité de données, donc attendre quelques minutes nous aide à nous concentrer sur le problème spécifique que vous signalez.

2.  Démarrer une deuxième copie de Visual Studio *sans solution ouverte*

3.  Dans la nouvelle copie de Visual Studio, ouvrez l’outil **Report a Problem**

4.  Suivez les étapes de [la façon de signaler un problème jusqu’à](/visualstudio/ide/how-to-report-a-problem-with-visual-studio-2017) ce que vous atteigniez l’étape « Fournir une trace et un tas de décharge (facultatif) ».

5.  Choisissez d’enregistrer la première copie de Visual Studio (celui qui rencontre un problème de performance) et de commencer à enregistrer.

    -   L’application Steps Recorder apparaîtra et commencera l’enregistrement.

    -   **Pendant l’enregistrement,** effectuer l’action problématique dans la première copie de Visual Studio. Il est difficile pour nous de corriger des problèmes de performance spécifiques s’ils n’apparaissent pas dans les délais enregistrés.

    -   Si l’action est inférieure à 30 secondes et peut être facilement répétée, répétez l’action pour démontrer davantage le problème.

    -   Dans la plupart des cas, une trace de 60 secondes est suffisante pour démontrer les problèmes, surtout si l’action problématique a duré (ou a été répétée) pendant plus de 30 secondes. La durée peut être ajustée au besoin pour capturer le comportement que vous souhaitez corriger.

6.  Cliquez sur "Stop Record" dans Steps Recorder dès que le fonctionnement lent ou l’événement CPU élevé que vous souhaitez signaler est terminé. Il peut prendre quelques minutes pour traiter la trace de performance.

7.  Une fois terminé, il y aura plusieurs pièces jointes à vos commentaires. Fixez tous les fichiers supplémentaires qui peuvent aider à reproduire le problème (un projet d’échantillon, des captures d’écran, des vidéos, etc.).

8.  Soumettez les commentaires.

Lors de l’enregistrement d’une trace de performances, si le fonctionnement lent ou le processeur élevé que vous signalez prend fin, puis arrêtez immédiatement l’enregistrement. Si trop d’informations sont recueillies, les informations les plus anciennes sont écrasées. Si le tracé n’est pas arrêté rapidement (en quelques secondes) après l’opération intéressante, les données utiles de trace seront écrasées.

N’attachez pas directement des traces de performance aux éléments de rétroaction existants sur le site Web de Developer Community. Demander/fournir des informations supplémentaires est un flux de travail pris en charge dans l’outil De rapport un problème intégré de Visual Studio. Si une trace de performance est nécessaire afin de résoudre un élément de rétroaction précédent, nous définirons l’état de l’élément de rétroaction à "Need More Info", qui peut être répondu de la même manière que la déclaration d’un nouveau problème. Pour obtenir des instructions détaillées, veuillez consulter [la section « Besoin de plus d’informations »](/visualstudio/ide/how-to-report-a-problem-with-visual-studio-2017?view=vs-2017#when-further-information-is-needed-need-more-info) dans le document d’un outil de signalement d’un problème.

> [!NOTE] 
> **Commentaires les plus précieux :** Pour presque toutes les lenteurs / problèmes de processeur élevé, la rétroaction la plus précieuse est une\*description de haut niveau de ce que vous essayiez de faire, avec la trace de performance (.etl.zip) qui capture le comportement pendant ce temps.

**Traces de performance avancées**

Les capacités de collecte de traces dans l’outil Report-a-problem sont suffisantes pour la plupart des scénarios. Mais il ya des moments où plus de contrôle sur la collecte de traces est nécessaire (par exemple, tracer avec une plus grande taille de tampon), auquel cas PerfView est un excellent outil à utiliser. Les étapes pour enregistrer manuellement la trace de performance à l’aide de l’outil PerfView peuvent être trouvées sur les [traces de performances d’enregistrement avec la page PerfView.](https://github.com/dotnet/roslyn/wiki/Recording-performance-traces-with-PerfView)

## <a name="out-of-process-issues"></a>Questions hors-processus

> [!NOTE]
> À partir de la version 16.3 de Visual Studio 2019, les journaux hors processus sont automatiquement attachés aux commentaires soumis à l’aide de l’outil Rapport a Problem. Toutefois, si le problème est directement reproductible, suivre les étapes ci-dessous pourrait tout de même aider à ajouter des informations supplémentaires pour aider à mieux diagnostiquer le problème.

Il existe un certain nombre de processus satellitaires qui fonctionnent parallèlement à Visual Studio et fournissent diverses fonctionnalités de l’extérieur du processus principal Visual Studio. Si une erreur se produit dans l’un de ces processus satellitaires, elle est généralement vue du côté visual Studio comme une «StreamJsonRpc.RemoteInvocationException» ou un «StreamJsonRpc.ConnectionLostException».

Ce qui rend ces types de questions les plus exploitables, c’est de fournir des journaux supplémentaires qui peuvent être collectés en suivant ces étapes :

1.  S’il s’agit d’une question directement reproductible, commencez par supprimer le dossier **%temp%/servicehub/logs.** Si vous ne pouvez pas reproduire ce problème s’il vous plaît garder ce dossier intact et ignorer les balles suivantes:

    -   Définir la variable de l’environnement mondial **ServiceHubTraceLevel** à **tous**
    -   Reproduisez le problème.

2.  Téléchargez le Microsoft Visual Studio et .NET Framework Log Collection Tool [ici](https://www.microsoft.com/download/details.aspx?id=12493).
3.  Exécutez l’outil. Cela produit un fichier zip à **%temp%/vslogs.zip**. Veuillez joindre ce fichier à vos commentaires.

## <a name="see-also"></a>Voir aussi

* [Options de commentaires de Visual Studio](../ide/feedback-options.md)
* [Signalez un problème avec Visual Studio pour Mac](/visualstudio/mac/report-a-problem)
* [Signaler un problème avec C++](/cpp/how-to-report-a-problem-with-the-visual-cpp-toolset)
* [Communauté des développeurs Visual Studio](https://developercommunity.visualstudio.com/)
* [Confidentialité des données de la communauté des développeurs](developer-community-privacy.md)
