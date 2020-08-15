---
title: Comment pouvez-vous augmenter les chances de résolution d’un problème de performances
description: Informations supplémentaires et meilleures pratiques pour envoyer des problèmes de performances dans Visual Studio
author: madskristensen
ms.author: madsk
ms.date: 11/19/2019
ms.topic: conceptual
ms.openlocfilehash: 50d1ed4edd2e1fa52661995f4d72466646dfd879
ms.sourcegitcommit: 577c905de52057a741e68c2ed168ea527813fda5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2020
ms.locfileid: "88250507"
---
# <a name="how-to-increase-the-chances-of-a-performance-issue-being-fixed"></a>Comment augmenter les chances de résolution d’un problème de performances

L’outil «[signaler un problème](/visualstudio/ide/how-to-report-a-problem-with-visual-studio?view=vs-2019)» est largement utilisé par les utilisateurs de Visual Studio pour signaler une série de problèmes. L’équipe Visual Studio parvient à faire face aux tendances de blocage et de lenteur des commentaires des utilisateurs et à résoudre les problèmes qui ont un impact sur un large SWATH d’utilisateurs. Plus un ticket de commentaires spécifique est exploitable, plus il est probable qu’il sera diagnostiqué et résolu rapidement par l’équipe du produit. Ce document décrit les meilleures pratiques lors de la création de rapports sur les incidents ou les problèmes de lenteur afin de les rendre plus exploitables.

## <a name="general-best-practices"></a>Bonnes pratiques générales

Visual Studio est une plateforme importante et complexe qui prend en charge une multitude de langages, de types de projets, de plateformes et bien plus encore. Son fonctionnement est une fonction des composants qui sont installés et actifs dans une session, les extensions installées, les paramètres de Visual Studio, la configuration de l’ordinateur et enfin la forme du code en cours de modification. Étant donné le nombre de variables, il est difficile de savoir si le rapport de problème d’un utilisateur présente le même problème sous-jacent qu’un rapport de problème d’un autre utilisateur, même si le symptôme visible est le même. Dans ce cas, voici quelques meilleures pratiques pour vous assurer que votre rapport de problèmes spécifique est susceptible de faire l’objet d’un diagnostic plus probable.

**Fournir le titre le plus spécifique possible**

Recherchez des signatures distinctes pour le problème signalé et incluez le plus grand nombre possible dans le titre. Si le titre est descriptif, il est moins probable que les utilisateurs avec des problèmes non liés (mais même symptôme superficiel) votent ou commentent votre ticket, ce qui complique le diagnostic de *votre* problème.

**En cas de doute, consigner un nouveau rapport de problème**

De nombreux problèmes peuvent ne pas avoir de signature distinctive ou de étapes à reproduire. Dans ce cas, un nouveau rapport est mieux adapté qu’un vote ou un commentaire sur un autre rapport, qui signale un *symptôme*extérieur similaire. Selon le type de rapport, incluez des fichiers de diagnostic supplémentaires dans votre rapport, comme décrit plus loin dans ce document.

**Meilleures pratiques spécifiques au problème**

Vous trouverez ci-dessous des problèmes difficiles à diagnostiquer sans bons fichiers de diagnostic. Après avoir identifié le cas qui décrit le mieux votre problème, suivez les étapes de commentaires spécifiques à ce cas.

- [Incidents :](#crashes) Un incident se produit lorsque le processus (Visual Studio) se termine de manière inattendue.

- Absence de [réponse :](#unresponsiveness) VS ne répond pas pendant une période prolongée.

- [Problèmes de lenteur :](#slowness-and-high-cpu-issues) Toute action spécifique dans VS est plus lente que souhaitée

- [UC élevée :](#slowness-and-high-cpu-issues) Périodes étendues d’utilisation intensive de l’UC de manière inattendue

- [Problèmes hors processus :](#out-of-process-issues) Un problème provoqué par un processus satellite Visual Studio

## <a name="crashes"></a>Crashes
Un incident se produit lorsque le processus (Visual Studio) se termine de manière inattendue.

**Blocages directement reproductibles**

Les blocages directement reproductibles sont des cas qui présentent toutes les caractéristiques suivantes :

- Peut être observé en suivant un ensemble d’étapes connu

- Peut être observé sur plusieurs ordinateurs (le cas échéant)

- Peut être reproduit dans un exemple de code ou un projet qui peut être lié ou fourni dans le cadre des commentaires (si les étapes impliquent l’ouverture d’un projet ou d’un document)

Pour ces problèmes, suivez les étapes de la section «[Comment signaler un problème](/visualstudio/ide/how-to-report-a-problem-with-visual-studio-2017)» et veillez à inclure les éléments suivants :

- Étapes à suivre pour reproduire le problème

- Un projet de reproduction autonome comme décrit ci-dessus. Si la reproduction autonome n’est pas possible, veuillez inclure :

  - Langage des projets ouverts (C \# , C++, etc.)

  - Genre de projet (application console, ASP.NET, etc.)

> [!NOTE]
> **Commentaires les plus importants :** Dans ce cas, les commentaires les plus précieux sont l’ensemble des étapes permettant de reproduire le problème, ainsi que l’exemple de code source.

**Incidents inconnus**

Si vous n’êtes pas sûr de ce qui est à l’origine de vos incidents ou s’ils semblent aléatoires, vous pouvez capturer des vidages localement chaque fois que Visual Studio se bloque et les joindre à des éléments de commentaires distincts. Pour enregistrer des dumps localement lorsque Visual Studio se bloque, exécutez les commandes suivantes dans une fenêtre de commande d’administrateur :

```
reg add "HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\Windows Error Reporting\LocalDumps\devenv.exe" /v DumpType /t REG_DWORD /d 2
reg add "HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\Windows Error Reporting\LocalDumps\devenv.exe" /v DumpCount /t REG_DWORD /d 2
reg add "HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\Windows Error Reporting\LocalDumps\devenv.exe" /v DumpFolder /t REG_SZ /d "C:\CrashDumps"

reg add "HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\Windows Error Reporting\LocalDumps\ServiceHub.RoslynCodeAnalysisService32.exe" /v DumpType /t REG_DWORD /d 2
reg add "HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\Windows Error Reporting\LocalDumps\ServiceHub.RoslynCodeAnalysisService32.exe" /v DumpCount /t REG_DWORD /d 2
reg add "HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\Windows Error Reporting\LocalDumps\ServiceHub.RoslynCodeAnalysisService32.exe" /v DumpFolder /t REG_SZ /d "C:\CrashDumps"

reg add "HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\Windows Error Reporting\LocalDumps\ServiceHub.RoslynCodeAnalysisService.exe" /v DumpType /t REG_DWORD /d 2
reg add "HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\Windows Error Reporting\LocalDumps\ServiceHub.RoslynCodeAnalysisService.exe" /v DumpCount /t REG_DWORD /d 2
reg add "HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\Windows Error Reporting\LocalDumps\ServiceHub.RoslynCodeAnalysisService.exe" /v DumpFolder /t REG_SZ /d "C:\CrashDumps"
```

Personnalisez le nombre de vidages et le dossier de vidage, le cas échéant. Pour plus d’informations sur ces [paramètres,](/windows/win32/wer/collecting-user-mode-dumps)consultez.

> [!NOTE]
> Les vidages capturés à l’aide du gestionnaire des tâches sont susceptibles d’avoir un nombre de bits incorrect, ce qui les rend moins utilisables. La procédure décrite ci-dessus est la méthode recommandée pour capturer un dump de tas. Si vous ne souhaitez pas utiliser le gestionnaire des tâches, fermez celui qui est en cours d’exécution, lancez le gestionnaire des tâches 32 bits (% windir% \\ syswow64 \\taskmgr.exe) et collectez un vidage du tas à partir de là.

> [!NOTE] 
> Chaque fichier dump produit par cette méthode aura une taille maximale de 4 Go. Veillez à définir DumpFolder sur un emplacement avec un espace disque suffisant ou à ajuster le DumpCount de manière appropriée.

Chaque fois que Visual Studio se bloque, il crée un fichier de vidage **devenv.exe. [ numéro]. dmp** à l’emplacement configuré.

Utilisez ensuite la section « signaler un problème... » de Visual Studio. fonctionnalité. Cela vous permettra d’attacher le vidage approprié.

1. Recherchez le fichier de vidage pour l’incident que vous signalez (recherchez un fichier avec l’heure de création correcte)

2. Si possible, compressez le fichier ( \* . zip) pour réduire sa taille avant de soumettre des commentaires

3. Suivez les étapes décrites dans la section «[Comment signaler un problème](/visualstudio/ide/how-to-report-a-problem-with-visual-studio-2017)», puis attachez le dump du tas à un nouvel élément de commentaires.

> [!NOTE] 
> **Commentaires les plus importants :** Dans ce cas, les commentaires les plus précieux sont le vidage du tas capturé au moment de l’incident.

## <a name="unresponsiveness"></a>Absence
VS ne répond pas pendant une période prolongée.

**Inactivité directement reproductible**

Comme décrit dans la section correspondante sur les incidents, pour les problèmes qui peuvent être facilement reproduits, vus sur plusieurs ordinateurs et qui peuvent être illustrés dans un petit exemple, les rapports de commentaires les plus précieux sont ceux qui incluent des étapes pour reproduire le problème et incluent un exemple de code source qui illustre le problème.

**Absence de réponse inconnue**

Si une absence de réponse se manifeste de manière imprévisible, à l’occurrence suivante, lancez une nouvelle instance de Visual Studio et signalez un problème à partir de cette instance.
Dans l' [écran « enregistrement »](/visualstudio/ide/how-to-report-a-problem-with-visual-studio?view=vs-2019#record-a-repro), veillez à sélectionner la session Visual Studio qui ne répond pas.

Si l’instance de Visual Studio qui ne répond pas a été lancée en mode administrateur, la deuxième instance doit également être lancée en mode administrateur.

>[!NOTE] 
> **Commentaires les plus importants :** Dans ce cas, les commentaires les plus précieux sont le vidage du tas capturé au moment de l’absence de réponse.

## <a name="slowness-and-high-cpu-issues"></a>Problèmes de lenteur et d’UC

Ce qui rend la lenteur de l’utilisation de l’UC ou le plus actionnable est une trace des performances capturée lorsque l’opération lente ou un événement d’UC élevé est en cours.

>[!NOTE] 
> Dans la mesure du possible, isolez chaque scénario dans un rapport de commentaires distinct et spécifique.
Par exemple, si la saisie et la navigation sont lentes, suivez les étapes ci-dessous une fois par problème. Cela permet à l’équipe de produit d’isoler la cause de problèmes spécifiques.

Pour obtenir les meilleurs résultats lors de la capture des performances, procédez comme suit :

1. S’il n’est pas déjà en cours d’exécution, une copie de Visual Studio s’ouvre et vous permet de reproduire le problème.

    - Que tout soit configuré pour reproduire le problème. Par exemple, si vous avez besoin d’un projet particulier à charger avec un fichier spécifique ouvert, assurez-vous que ces deux étapes sont terminées avant de continuer.

    - Si vous ne signalez *pas* de problème spécifique au chargement d’une solution, essayez d’attendre 5-10 minutes (ou plus, en fonction de la taille de la solution) après avoir ouvert la solution avant d’enregistrer le suivi des performances. Le processus de chargement de la solution produit une grande quantité de données. l’attente de quelques minutes nous aide à nous concentrer sur le problème spécifique que vous signalez.

2. Démarrer une seconde copie de Visual Studio sans *ouvrir de solution*

3. Dans la nouvelle copie de Visual Studio, ouvrez l’outil **signaler un problème** .

4. Suivez les étapes de la section [Comment signaler un problème](/visualstudio/ide/how-to-report-a-problem-with-visual-studio-2017) jusqu’à ce que vous atteigniez l’étape « fournir une trace et un dump de tas (facultatif) ».

5. Choisissez d’enregistrer la première copie de Visual Studio (qui rencontre un problème de performances) et de démarrer l’enregistrement.

    - L’application d’enregistrement des étapes s’affiche et commence l’enregistrement.

    - **Pendant l’enregistrement,** effectuez l’action problématique dans la première copie de Visual Studio. Il est difficile pour nous de corriger des problèmes de performances spécifiques s’ils n’apparaissent pas dans le temps enregistré.

    - Si l’action est plus petite que 30 secondes et peut être répétée facilement, répétez l’action pour mieux illustrer le problème.

    - Dans la plupart des cas, une trace de 60 secondes suffit pour démontrer les problèmes, en particulier si l’action problématique a été retardée (ou a été répétée) pendant plus de 30 secondes. La durée peut être ajustée si nécessaire pour capturer le comportement que vous souhaitez corriger.

6. Cliquez sur « arrêter l’enregistrement » dans l’enregistreur d’actions dès que l’opération lente ou l’événement d’UC élevé que vous souhaitez signaler est terminé. Le traitement de la trace des performances peut prendre quelques minutes.

7. Une fois l’opération terminée, il y aura plusieurs pièces jointes à vos commentaires. Joignez tous les fichiers supplémentaires susceptibles de vous aider à reproduire le problème (un exemple de projet, des captures d’écran, des vidéos, etc.).

8. Envoyez les commentaires.

Lors de l’enregistrement d’un suivi des performances, si la lenteur de l’opération ou du processeur que vous signalez est en fin de compte, arrêtez immédiatement l’enregistrement. Si un trop grand nombre d’informations sont collectées, les informations les plus anciennes sont remplacées. Si le suivi n’est pas arrêté peu de temps (en quelques secondes) après l’opération intéressante, les données de trace utiles seront remplacées.

N’attachez pas directement les traces de performances aux éléments de commentaires existants sur le site Web de la communauté des développeurs. Demander/fournir des informations supplémentaires est un flux de travail pris en charge dans l’outil signaler un problème intégré de Visual Studio. Si un suivi des performances est nécessaire pour résoudre un élément de commentaires précédent, nous allons définir l’état de l’élément de commentaires sur « besoin d’informations supplémentaires », qui peut être répondu de la même façon que pour signaler un nouveau problème. Pour obtenir des instructions détaillées, reportez-vous à la [section « besoin d’informations supplémentaires »](/visualstudio/ide/how-to-report-a-problem-with-visual-studio-2017?view=vs-2017#when-further-information-is-needed-need-more-info) dans le document signaler un problème de l’outil.

> [!NOTE] 
> **Commentaires les plus importants :** Pour presque tous les problèmes de lenteur ou de processeur, les commentaires les plus précieux sont une description de haut niveau de ce que vous tentiez de faire, ainsi que la trace de performances ( \*.etl.zip) qui capture le comportement pendant ce temps.

**Suivis de performances avancés**

Les fonctionnalités de collecte de trace de l’outil rapport-a-problem sont suffisantes pour la plupart des scénarios. Toutefois, il existe des cas où un plus grand contrôle de la collection de suivis est nécessaire (par exemple, trace avec une plus grande taille de mémoire tampon), auquel cas PerfView est un excellent outil à utiliser. Les étapes pour l’enregistrement manuel des traces de performances à l’aide de l’outil PerfView se trouvent dans la page [enregistrement des traces de performances avec PerfView](https://github.com/dotnet/roslyn/wiki/Recording-performance-traces-with-PerfView) .

## <a name="out-of-process-issues"></a>Problèmes hors processus

> [!NOTE]
> À compter de Visual Studio 2019 version 16,3, les journaux hors processus sont automatiquement joints aux commentaires envoyés à l’aide de l’outil signaler un problème. Toutefois, si le problème est directement reproductible, le fait de suivre les étapes ci-dessous peut vous aider à ajouter des informations supplémentaires pour mieux diagnostiquer le problème.

Il existe un certain nombre de processus satellites qui s’exécutent parallèlement à Visual Studio et fournissent différentes fonctionnalités à partir de l’extérieur du processus principal de Visual Studio. Si une erreur se produit dans l’un de ces processus satellites, elle est généralement visible côté Visual Studio sous la forme d’un « StreamJsonRpc. RemoteInvocationException » ou d’un « StreamJsonRpc. ConnectionLostException ».

Ce qui rend ces types de problèmes les plus exploitables consiste à fournir des journaux supplémentaires qui peuvent être collectés en procédant comme suit :

1. S’il s’agit d’un problème directement reproductible, commencez par supprimer le dossier **% temp%/servicehub/logs** . Si vous ne pouvez pas reproduire ce problème, conservez ce dossier intact et ignorez les puces suivantes :

    - Définir la variable d’environnement globale **ServiceHubTraceLevel** sur **All**
    - Reproduisez le problème.

2. Téléchargez le Microsoft Visual Studio et .NET Framework outil de collecte de journaux [ici](https://www.microsoft.com/download/details.aspx?id=12493).
3. Exécutez l’outil. Cela génère un fichier zip dans **% temp%/vslogs.zip**. Veuillez joindre ce fichier à vos commentaires.

## <a name="see-also"></a>Voir aussi

* [Options de commentaires de Visual Studio](../ide/feedback-options.md)
* [Signaler un problème avec Visual Studio pour Mac](/visualstudio/mac/report-a-problem)
* [Signaler un problème avec C++](/cpp/how-to-report-a-problem-with-the-visual-cpp-toolset)
* [Communauté des développeurs Visual Studio](https://developercommunity.visualstudio.com/)
* [Confidentialité des données de la communauté des développeurs](developer-community-privacy.md)
