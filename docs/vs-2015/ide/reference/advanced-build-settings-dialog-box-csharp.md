---
title: Paramètres de génération avancés, boîte de dialogue (C#) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- cs.AdvancedBuildSettings
helpviewer_keywords:
- Build options [C#], advanced
ms.assetid: 141f2dee-1563-4ce6-ba37-32920b082519
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 38f4d233c8804bec91d2f7dfd2dc34c6879e8be9
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72651734"
---
# <a name="advanced-build-settings-dialog-box-c"></a>Paramètres de génération avancés, boîte de dialogue (C#)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Utilisez la boîte de dialogue **Paramètres de génération avancés** du **Concepteur de projet** pour spécifier les propriétés avancées de configuration de build du projet. Cette boîte de dialogue s’applique aux projets [!INCLUDE[csprcs](../../includes/csprcs-md.md)] uniquement.

## <a name="general"></a>Général
 Les options suivantes permettent de définir des paramètres généraux avancés.

 **Version du langage** Spécifie la version du langage à utiliser. L’ensemble de fonctionnalités est différent pour chacune des versions. Cette option peut donc être utilisée pour forcer le compilateur à autoriser uniquement un sous-ensemble des fonctionnalités implémentées, ou à activer uniquement les fonctionnalités conformes à une norme existante. Ce paramètre a les options suivantes :

- **ISO-1**

   Cible les fonctionnalités conformes à la norme ISO-1.

- **default**

   Cible la version actuelle.

  Pour plus d’informations, consultez [/langversion (options du compilateur C#)](https://msdn.microsoft.com/library/3fb00b05-a0ff-4782-b313-13a4c0f62d94).

  **Rapport d’erreurs du compilateur interne** Spécifie s’il faut signaler les erreurs du compilateur à Microsoft. Si la valeur est **prompt** (valeur par défaut), une invite s’affiche en cas d’erreur interne du compilateur, et vous donne la possibilité d’envoyer un rapport d’erreurs par voie électronique à Microsoft. Si la valeur est **send**, un rapport d’erreurs est envoyé automatiquement. Si la valeur est **queue**, les rapports d’erreurs sont mis en file attente. Si la valeur est **none**, l’erreur est signalée uniquement dans la sortie de texte du compilateur. Pour plus d’informations, consultez [/errorreport (options du compilateur C#)](https://msdn.microsoft.com/library/bd0e7493-b79d-4369-9c3f-ba26ebdfbedf).

  **Vérifier le dépassement de capacité positif/négatif** Spécifie si une instruction arithmétique sur les entiers qui ne figure pas dans la portée des mots clés [checked](https://msdn.microsoft.com/library/718a1194-988d-48a3-b089-d6ee8bd1608d) ou [unchecked](https://msdn.microsoft.com/library/0c021f7c-923f-4b3d-a58f-55336f5ac27e) et qui produit une valeur en dehors de la plage du type de données provoque une exception Runtime. Pour plus d’informations, consultez l' [option/Checked (C# options du compilateur)](https://msdn.microsoft.com/library/fb7475d3-e6a6-4e6d-b86c-69e7a74c854b).

  **Ne pas référencer mscorlib.dll** Spécifie si mscorlib.dll doit être importé dans votre programme, en définissant l’intégralité de l’espace de noms <xref:System>. Cochez cette case pour définir ou créer vos propres objets et espaces de noms <xref:System>. Pour plus d’informations, consultez [/nostdlib (options du compilateur C#)](https://msdn.microsoft.com/library/ec197989-fa49-4725-a455-e06b551eb65f).

## <a name="output"></a>Sortie
 Les options suivantes permettent de spécifier des options de sortie avancées.

 **Informations de débogage** Spécifie le type d’informations de débogage générées par le compilateur. Pour plus d’informations sur la configuration des performances de débogage d’une application, consultez [Simplification du débogage d’une image](https://msdn.microsoft.com/library/7d90ea7a-150f-4f97-98a7-f9c26541b9a3). Ce paramètre a les options suivantes :

- **none**

   Spécifie que les informations de débogage ne doivent pas être générées.

- **full**

   Permet d’attacher un débogueur au programme en cours d’exécution.

- **pdbonly**

   Active le débogage du code source lorsque le programme est démarré dans le débogueur, mais affiche uniquement un assembleur quand le programme en cours d’exécution est attaché au débogueur.

  Pour plus d’informations, consultez [/debug (options du compilateur C#)](https://msdn.microsoft.com/library/e2b48c07-01bc-45cc-a52c-92e9085eb969).

  **Alignement des fichiers** Spécifie la taille des sections dans le fichier de sortie. Les valeurs valides sont **512**, **1024**, **2048**, **4096** et **8192**. Ces valeurs sont mesurées en octets. Chaque section est alignée sur une limite qui est un multiple de cette valeur, affectant ainsi la taille du fichier de sortie. Pour plus d’informations, consultez [/filealign (options du compilateur C#)](https://msdn.microsoft.com/library/15cf1c98-3798-4ced-9f08-60619308a073).

  **Adresse de base** de la dll Spécifie l’adresse de base préférée à laquelle charger une DLL. L’adresse de base par défaut d’une DLL est définie par le common language runtime [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]. Pour plus d’informations, consultez [/baseaddress (options du compilateur C#)](https://msdn.microsoft.com/library/ce13c965-dfe4-4433-94f5-63b476e3a608).

## <a name="see-also"></a>Voir aussi
 [Options du compilateur C#](https://msdn.microsoft.com/library/d3403556-1816-4546-a782-e8223a772e44) [Générer, page du Concepteur de projets (C#)](../../ide/reference/build-page-project-designer-csharp.md)
