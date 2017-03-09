---
title: "Paramètres de génération avancés, boîte de dialogue (C#) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- cs.AdvancedBuildSettings
helpviewer_keywords:
- Build options [C#], advanced
ms.assetid: 141f2dee-1563-4ce6-ba37-32920b082519
caps.latest.revision: 13
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: 5658ecf52637a38bc3c2a5ad9e85b2edebf7d445
ms.openlocfilehash: 82ec5d2db35da72beb017e15d1c271f751b5f56b
ms.lasthandoff: 02/22/2017

---
# <a name="advanced-build-settings-dialog-box-c"></a>Paramètres de génération avancés, boîte de dialogue (C#)
Utilisez la boîte de dialogue **Paramètres de génération avancés** du **Concepteur de projet** pour spécifier les propriétés avancées de configuration de build du projet. Cette boîte de dialogue s’applique aux projets [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] uniquement.  
  
## <a name="general"></a>Général  
 Les options suivantes permettent de définir des paramètres généraux avancés.  
  
 **Version du langage**  
 Spécifie la version du langage à utiliser. L’ensemble de fonctionnalités est différent pour chacune des versions. Cette option peut donc être utilisée pour forcer le compilateur à autoriser uniquement un sous-ensemble des fonctionnalités implémentées, ou à activer uniquement les fonctionnalités conformes à une norme existante. Ce paramètre a les options suivantes :  
  
-   **ISO-1**  
  
     Cible les fonctionnalités conformes à la norme ISO-1.  
  
-   **default**  
  
     Cible la version actuelle.  
  
 Pour plus d’informations, consultez l’article [/langversion (C# Compiler Options) (/langversion [Options du compilateur C#])](/dotnet/csharp/language-reference/compiler-options/langversion-compiler-option).  
  
 **Rapport d’erreurs du compilateur interne**  
 Spécifie s’il faut signaler les erreurs du compilateur à Microsoft. Si la valeur est **prompt** (valeur par défaut), une invite s’affiche en cas d’erreur interne du compilateur, et vous donne la possibilité d’envoyer un rapport d’erreurs par voie électronique à Microsoft. Si la valeur est **send**, un rapport d’erreurs est envoyé automatiquement. Si la valeur est **queue**, les rapports d’erreurs sont mis en file attente. Si la valeur est **none**, l’erreur est signalée uniquement dans la sortie de texte du compilateur. Pour plus d’informations, consultez l’article [/errorreport (C# Compiler Options) (/errorreport [Options du compilateur C#])](/dotnet/csharp/language-reference/compiler-options/errorreport-compiler-option).  
  
 **Vérifier les dépassements de capacité arithmétiques positifs et négatifs**  
 Spécifie si une instruction arithmétique entière qui n’est pas dans la portée des mots clés [checked](/dotnet/csharp/language-reference/keywords/checked) ou [unchecked](/dotnet/csharp/language-reference/keywords/unchecked), et dont la valeur n’est pas comprise dans la plage du type de données, doit provoquer la levée d’une exception au moment de l’exécution. Pour plus d’informations, consultez [/checked (options du compilateur C#)](/dotnet/csharp/language-reference/compiler-options/checked-compiler-option).  
  
 **Ne pas référencer mscorlib.dll**  
 Spécifie si mscorlib.dll doit être importé dans votre programme, en définissant l’intégralité de l’espace de noms <xref:System>. Cochez cette case pour définir ou créer vos propres objets et espaces de noms <xref:System>. Pour plus d’informations, consultez l’article [/nostdlib (C# Compiler Options) (/nostdlib [Options du compilateur C#])](/dotnet/csharp/language-reference/compiler-options/nostdlib-compiler-option).  
  
## <a name="output"></a>Sortie  
 Les options suivantes permettent de spécifier des options de sortie avancées.  
  
 **Informations de débogage**  
 Indique le type d'informations de débogage générées par le compilateur. Pour plus d’informations sur la configuration des performances de débogage d’une application, consultez [Simplification du débogage d’une image](http://msdn.microsoft.com/Library/7d90ea7a-150f-4f97-98a7-f9c26541b9a3). Ce paramètre a les options suivantes :  
  
-   **none**  
  
     Spécifie que les informations de débogage ne doivent pas être générées.  
  
-   **full**  
  
     Permet d’attacher un débogueur au programme en cours d’exécution.  
  
-   **pdbonly**  
  
     Active le débogage du code source lorsque le programme est démarré dans le débogueur, mais affiche uniquement un assembleur quand le programme en cours d’exécution est attaché au débogueur.  
  
 Pour plus d’informations, consultez l’article [/debug (C# Compiler Options) (/debug [Options du compilateur C#])](/dotnet/csharp/language-reference/compiler-options/debug-compiler-option).  
  
 **Alignement des fichiers**  
 Spécifie la taille des sections dans le fichier de sortie. Les valeurs valides sont **512**, **1024**, **2048**, **4096** et **8192**. Ces valeurs sont mesurées en octets. Chaque section est alignée sur une limite qui est un multiple de cette valeur, affectant ainsi la taille du fichier de sortie. Pour plus d’informations, consultez l’article [/filealign (C# Compiler Options) (/filealign [Options du compilateur C#])](/dotnet/csharp/language-reference/compiler-options/filealign-compiler-option).  
  
 **Adresse de base de la DLL**  
 Spécifie l'adresse de base préférée à laquelle charger une DLL. L’adresse de base par défaut d’une DLL est définie par le common language runtime [!INCLUDE[dnprdnshort](../../code-quality/includes/dnprdnshort_md.md)]. Pour plus d’informations, consultez l’article [/baseaddress (C# Compiler Options) (/baseaddress [Options du compilateur C#])](/dotnet/csharp/language-reference/compiler-options/baseaddress-compiler-option).  
  
## <a name="see-also"></a>Voir aussi  
 [Options du compilateur C#](/dotnet/csharp/language-reference/compiler-options/index)   
 [Générer, page du Concepteur de projets (C#)](../../ide/reference/build-page-project-designer-csharp.md)
