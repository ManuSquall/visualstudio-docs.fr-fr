---
title: Commandes devinit
description: Détails sur l’utilisation des commandes devinit pour installer des composants.
ms.date: 08/28/2020
ms.topic: reference
author: andysterland
ms.author: andster
manager: jillfra
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.prod: visual-studio-windows
ms.technology: devinit
ms.openlocfilehash: 1a0bd657d9612bde05a820a591c2ab2c1cfdaad3
ms.sourcegitcommit: 09d1f5cef5360cdc1cdfd4b22a1a426b38079618
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "91005530"
---
# <a name="devinit-commands"></a>commandes devinit

## <a name="init"></a>Init

```console
> devinit init
```

Initialisez l’environnement en exécutant les outils spécifiés dans un [_.devinit.jssur_](devinit-json.md) le fichier dans le répertoire de travail actuel.  

### <a name="options-for-init"></a>Options pour init

Options facultatives pour la `devinit init` commande.

| Argument             | Obligatoire | Description                                                               |
|----------------------|----------|---------------------------------------------------------------------------|
| -f,--file           | Non       | Chemin d’accès à la _.devinit.jssur_ le fichier.                                         |
| --erreur-action       | Non       | Spécifie comment gérer les erreurs. Options : arrêter, ignorer, continuer (par défaut).|
| -v,--commentaires         | Non       | Émet une sortie détaillée.                                                      |
| -n,--à sec         | Non       | Série sèche.                                                                  |

## <a name="run"></a>Exécuter

```console
> devinit run -t <toolname>
```

Exécute l’outil spécifique, les paramètres sont répertoriés ci-dessous. Consultez [la documentation](devinit-tool-list.md) de chaque outil pour une utilisation spécifique.

### <a name="options-for-run"></a>Options pour l’exécution

Options de la `devinit run` commande.

| Argument                                  | Obligatoire | Description                                                                          |
|-------------------------------------------|----------|--------------------------------------------------------------------------------------|
| outil-t,--                                 | Oui      | Obligatoire. Nom de l'outil.                                                             |
| -i,--entrée                                | Non       | Valeur d’entrée de l’outil. Par exemple, un nom de fichier, un package ou un nom.                           |
| --erreur-action                            | Non       | Spécifie comment gérer les erreurs d’outil : arrêter, ignorer, continuer. La valeur par défaut consiste à arrêter. |
| -v,--commentaires                              | Non       | Émet une sortie détaillée.                                                                 |
| -n,--à sec                              | Non       | Série sèche.                                                                             |
| --&lt;arg1 &gt; &lt; Arg2 &gt; &lt; argN&gt;  | Non       | Arguments de ligne de commande supplémentaires pour l’outil.                                       |

#### <a name="--file-argument"></a>--argument de fichier

Spécifie le chemin d’accès à la _devinit.jssur le fichier. Si – file n’est pas spécifié, nous recherchons un fichier par défaut aux emplacements suivants :

* {Current-Directory} \\.devinit.js
* {Current-Directory} \\ . devinit \\.devinit.js

Remarque : les chemins d’accès sans le début du `.` répertoire ou du nom de fichier correspondent également.

#### <a name="--error-action-argument"></a>--erreur-argument d’action

Spécifie l’action à entreprendre si un outil retourne un code de sortie différent de zéro. Les valeurs valides sont les suivantes :

| Argument | Description                                                                                                                                                                                                                                                                           |
|----------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| continue | Continuez à traiter d’autres outils après l’émission d’une erreur vers une erreur standard. Le code de sortie de devinit.exe est différent de zéro (échec). Ce comportement est similaire à l’action d’arrêt de l’erreur, mais le traitement se poursuit. `continue` est l’action d’erreur par défaut pour la commande init.              |
| ignore   | Continuer le traitement d’autres outils après l’émission d’un avertissement vers la sortie standard. Le code de sortie du processus DevInit doit toujours être égal à zéro (réussite). Le `ignore` paramètre ignore toutes les erreurs.                                                                                                      |
| stop     | Envoie une erreur à l’erreur standard et arrête les outils de traitement. Le code de sortie de devinit.exe est différent de zéro (échec). Cela est similaire à l’action continuer l’erreur, mais le traitement s’arrête à la première erreur rencontrée. `stop` est l’action d’erreur par défaut pour toutes les commandes, à l’exception de init. |

#### <a name="--dry-run-switch"></a>--commutateur à exécution à sec

Commandes de l’outil ECHO qui sont exécutées, mais n’exécutent aucun outil. 

#### <a name="--verbose-switch"></a>--commutateur détaillé

Émet la sortie détaillée vers la sortie standard. Si l’outil à exécuter prend en charge une option détaillée, propage le commutateur détaillé à l’outil.

#### <a name="note-on-additional-command-line-arguments"></a>Remarque sur les arguments de ligne de commande supplémentaires

L’utilisation d’un `<arg>` qui inclut un espace dans sa valeur doit inclure une paire supplémentaire de guillemets d’échappement.

```console
> devinit run -t <toolname> -<somearg> "<some value>"
```

Pour installer dotnet dans un répertoire spécifique `C:\Program Files\dotnet` :

```console
> devinit run -t require-dotnetcoresdk --"-InstallDir \"C:\Program Files\dotnet\""
```

## <a name="list"></a>List

```console
> devinit list
```

Affiche la liste de tous les outils disponibles.

## <a name="show"></a>Afficher

```console
> devinit show -t <toolname>
```

| Argument       | Obligatoire | Description                                                                          |
|----------------|----------|--------------------------------------------------------------------------------------|
| outil-t,--      | Oui      | Obligatoire. Nom de l'outil.                                                             |

Imprime les informations d’aide pour un outil donné.

## <a name="version"></a>Version

```console
> devinit version
```

Imprime les informations de version actuelles pour devinit.

## <a name="help"></a>Aide

```console
> devinit help
> devinit help list
```

Imprime le texte d’aide pour devinit ou pour une commande spécifique `devinit <command>` .
 