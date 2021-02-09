---
title: Exemple Dia2dump | Microsoft Docs
ms.date: 07/24/2018
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- sample applications [DIA SDK]
- Dia2dump sample [DIA SDK]
ms.assetid: 492c0893-7043-452f-a020-890a47230d20
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: fee6f04b3ee0aefe0aac99f8079e2f31733ce08b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99865418"
---
# <a name="dia2dump-sample"></a>Dia2dump, exemple

L’exemple Dia2dump montre comment utiliser le kit de développement logiciel (SDK) Microsoft Debug interface Access (DIA SDK) pour interroger un fichier PDB afin d’obtenir des informations.

L’exemple Dia2dump est installé avec Visual Studio et contient la solution et les fichiers sources. L’exécutable compilé s’exécute à partir de la ligne de commande. Il peut afficher le contenu d’un fichier de base de données du programme (. pdb) entier ou uniquement les sections qui vous intéressent.

## <a name="install-the-sample"></a>Installer l’exemple

L’exemple est installé lorsque vous choisissez la charge de travail **développement Desktop en C++** dans la Visual Studio installer. Pour plus d’informations sur l’installation de Visual Studio et sur la sélection de charges de travail spécifiques et de composants individuels, consultez [installer Visual Studio](../../install/install-visual-studio.md).

Une fois installé, l’exemple se trouve dans le répertoire d’installation de Visual Studio, dans un sous-répertoire nommé \DIA SDK\Samples\DIA2Dump.

## <a name="build-the-sample"></a>Générer l’exemple

Par défaut, le répertoire d’installation est un répertoire protégé. Cela signifie que vous devez utiliser une invite de commandes développeur avec élévation de privilèges ou une instance de Visual Studio pour créer et modifier l’exemple de solution à cet emplacement. Pour simplifier la génération, nous vous recommandons de commencer par copier les fichiers du répertoire d’exemple vers un autre répertoire, tel qu’un dossier dans votre dossier documents, puis de générer l’exemple.

### <a name="to-build-the-dia2dump-sample-in-visual-studio"></a>Pour générer l’exemple Dia2Dump dans Visual Studio

1. Ouvrez le fichier DIA2Dump. sln dans Visual Studio. Si vous n’avez pas copié la solution dans un autre répertoire, vous pouvez être invité à redémarrer Visual Studio avec des autorisations élevées.

1. Dans **Explorateur de solutions**, sélectionnez le projet Dia2Dump (pas la solution).

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Utilisation des propriétés de projet](/cpp/build/working-with-project-properties).

1. Ouvrez la page de propriétés général de **Propriétés de configuration**  >  **C/C++**  >   .

1. Dans la propriété **autres répertoires Include** , choisissez le contrôle DropDown, puis choisissez **modifier**.

1. Dans la boîte de dialogue **autres répertoires Include** , dans le champ modifier, entrez le `$(VSInstallDir)DIA SDK\include` répertoire. Ajoutez ce répertoire pour garantir que le compilateur peut trouver le fichier Dia2. h. Choisissez **OK** pour enregistrer vos modifications.

1. Choisissez **OK** pour enregistrer les modifications apportées aux propriétés du projet.

1. Dans le menu **générer** , choisissez **régénérer la solution**. Par défaut, Visual Studio génère une version de débogage de l’exemple, située dans un sous-répertoire de débogage du répertoire de la solution.

1. Fermez Visual Studio.

### <a name="to-build-the-dia2dump-sample-at-the-command-line"></a>Pour générer l’exemple Dia2Dump à partir de la ligne de commande

1. Dans une fenêtre d’invite de commandes développeur, accédez au répertoire dans lequel vous avez copié les exemples de fichiers. Si vous n’avez pas copié l’exemple dans un autre répertoire, vous devez utiliser une fenêtre d’invite de commandes développeur avec élévation de privilèges (exécuter en tant qu’administrateur).

1. Entrez la commande `nmake makefile` pour générer la configuration Debug par défaut de dia2dump.exe.

## <a name="run-the-dia2dump-sample"></a>Exécuter l’exemple Dia2Dump

Dia2Dump.exe s’appuie sur le serveur COM *version*. dll MSDIA pour fournir ses services. À compter de Visual Studio 2015, la version est msdia140.dll. Si le serveur COM MSDIA *version*. dll n’est pas initialisé, vous devez l’inscrire pour que dia2dump.exe puisse fonctionner. Le répertoire DIA SDK possède un sous-répertoire bin qui contient la version x86 de la DLL. Une version pour les machines d’architecture x64 est dans bin\amd64, et une version pour ARM est dans bin\arm. Pour inscrire la dll, ouvrez une fenêtre d’invite de commandes développeur avec élévation de privilèges, puis accédez au répertoire qui contient la version de votre architecture d’ordinateur. Entrez la commande `regsvr32 msdia140.dll` pour inscrire le serveur com.

### <a name="to-run-the-sample"></a>Exécution de l'exemple

1. Ouvrez une invite de commandes et accédez au répertoire qui contient les dia2dump.exe que vous avez générés.

1. Entrez la commande `dia2dump filename` où *filename* est le nom d’un fichier PDB à examiner. Si le fichier PDB se trouve dans un autre répertoire, utilisez le chemin d’accès complet au fichier en tant que *nom* de fichier. Cette commande répertorie toutes les données du fichier PDB.

1. Dia2Dump offre d’autres options pour afficher uniquement les informations sélectionnées. Utilisez la `dia2dump -?` commande pour répertorier toutes les options disponibles.

## <a name="see-also"></a>Voir aussi

- [Porter, migrer et mettre à niveau des projets Visual Studio](../../porting/port-migrate-and-upgrade-visual-studio-projects.md)
