---
title: Utilisation des C++ contrôleurs d’instructions de base | Microsoft Docs
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.date: 11/15/2016
ms.topic: conceptual
ms.assetid: a2098fd9-8334-4e95-9b8d-bc3da689d9e3
caps.latest.revision: 11
author: mikeblome
ms.author: mblome
manager: jillfra
ms.openlocfilehash: ccc44b77c4524e7d707ce3fe407d204d729017ff
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74291236"
---
# <a name="using-the-c-core-guidelines-checkers"></a>Utilisation des vérificateurs C++ Core Guidelines
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Les C++ directives principales sont un ensemble portable d’instructions, de règles et de meilleures pratiques concernant le C++ codage créé C++ par des experts et des concepteurs.  Visual Studio prend désormais en charge les packages de compléments qui créent des règles supplémentaires pour les outils d’analyse du code afin de C++ vérifier la conformité de votre code avec les recommandations principales et de suggérer des améliorations.  
  
## <a name="the-c-core-guidelines-project"></a>Le C++ projet de recommandations principales  
 Créé par Bjarne Stroustrup et d’autres, C++ les recommandations de base sont un guide d' C++ utilisation de la sécurité moderne et efficace. Les directives insistent sur la sécurité des types statiques et la sécurité des ressources. Ils identifient les moyens d’éliminer ou de réduire les parties les plus sujettes aux erreurs du langage, et de vous suggérer comment rendre votre code plus simple et plus performant de manière fiable. Ces recommandations sont gérées par la C++ base standard. Pour en savoir plus, consultez la documentation, C++ [ C++ les instructions principales](http://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines)et accédez aux fichiers de projet de base de documentation sur [GitHub](https://github.com/isocpp/CppCoreGuidelines).  
  
 Microsoft prend en C++ charge les recommandations de base C++ en créant des ensembles de règles d’analyse du code de vérification de base que vous pouvez ajouter à vos projets à l’aide d’un package NuGet. Le package est nommé Microsoft. CppCoreCheck et est disponible sur [https://www.nuget.org/packages/Microsoft.CppCoreCheck](https://www.nuget.org/packages/Microsoft.CppCoreCheck). Pour ce package, vous devez avoir au moins Visual Studio 2015 avec la mise à jour 1 installée.  
  
 Le package installe également un autre package en tant que dépendance, une bibliothèque de prise en charge des instructions en en-tête uniquement (GSL). Le portail GSL est également disponible sur GitHub à l’adresse [https://github.com/Microsoft/GSL](https://github.com/Microsoft/GSL).  
  
## <a name="enable-the-c-core-check-guidelines-in-code-analysis"></a>Activer les C++ instructions de contrôle de base dans l’analyse du code  
 Pour activer les C++ outils d’analyse du code de vérification de base, installez le package NuGet Microsoft C++ . CppCoreCheck dans chaque projet que vous souhaitez vérifier dans Visual Studio.  
  
#### <a name="to-add-the-microsoftcppcorecheck-package-to-your-project"></a>Pour ajouter le package Microsoft. CppCoreCheck à votre projet  
  
1. Dans **Explorateur de solutions**, cliquez avec le bouton droit pour ouvrir le menu contextuel de votre projet dans la solution à laquelle vous souhaitez ajouter le package. Sélectionnez **gérer les packages NuGet** pour ouvrir le **Gestionnaire de package NuGet**.  
  
2. Dans la fenêtre **Gestionnaire de package NuGet** , recherchez Microsoft. CppCoreCheck.  
  
    ![La fenêtre du gestionnaire de package NuGet affiche le package CppCoreCheck](../code-quality/media/cppcorecheck-nuget-window.PNG "CPPCoreCheck_Nuget_Window")  
  
3. Sélectionnez le package Microsoft. CppCoreCheck, puis cliquez sur le bouton **installer** pour ajouter les règles à votre projet.  
  
   Le package NuGet ajoute un fichier MSBuild. targets supplémentaire à votre projet qui est appelé lorsque vous activez l’analyse du code sur votre projet. Ce fichier. targets ajoute C++ les règles de contrôle de base en tant qu’extension supplémentaire à l’outil d’analyse du code Visual Studio.  
  
   Vous pouvez activer l’analyse du code sur votre projet en activant la case à cocher **activer l’analyse du code sur la build** dans la section **analyse du code** de la boîte de dialogue **pages de propriétés** de votre projet.  
  
   ![Page de propriétés pour les paramètres généraux de l’analyse du code](../code-quality/media/cppcorecheck-codeanalysis-general.png "CPPCoreCheck_CodeAnalysis_General")  
  
   Les C++ règles de contrôle de base font partie des ensembles de règles par défaut qui s’exécutent lorsque l’analyse du code est activée. Étant donné C++ que les règles de contrôle de base sont en cours de développement, certaines règles peuvent ne pas être prêtes à être utilisées sur tout le code, mais peuvent être informatives au cours du développement. Ces règles sont publiées comme expérimentales. Vous pouvez choisir d’exécuter ou non les règles publiées ou expérimentales dans les propriétés de votre projet.  
  
   ![Page de propriétés pour les paramètres des extensions d’analyse du code](../code-quality/media/cppcorecheck-codeanalysis-extensions.png "CPPCoreCheck_CodeAnalysis_Extensions")  
  
   Pour activer ou désactiver les C++ ensembles de règles de vérification de base, ouvrez la boîte de dialogue **pages de propriétés** de votre projet. Sous **Propriétés de configuration**, développez **analyse du code**, **Extensions**. Dans le contrôle de liste déroulante en regard de **activer C++ la vérification principale (publiée)** ou **activer C++ la vérification principale (expérimental)** , choisissez **Oui** ou **non**. Cliquez sur **OK** ou sur **appliquer** pour enregistrer vos modifications.  
  
## <a name="check-types-bounds-and-lifetimes"></a>Vérifier les types, les limites et les durées de vie  
 Le C++ package de contrôle principal contient actuellement des contrôleurs pour la sécurité de [type](http://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines#SS-type), les [limites de sécurité](http://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines#SS-bounds)et les profils de sécurité de [durée de vie](http://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines#SS-lifetime) .  
  
 Voici un exemple des types de problèmes que les C++ règles de contrôle de base peuvent trouver :  
  
```cpp  
// CoreCheckExample.cpp  
// Add CppCoreCheck package and enable code analysis in build for warnings.  
  
int main()  
{  
    int arr[10];           // warning C26494  
    int* p = arr;          // warning C26485  
  
    [[gsl::suppress(bounds.1)]] // This attribute suppresses Bounds rule #1  
    {  
        int* q = p + 1;    // warning C26481 (suppressed)  
        p = q++;           // warning C26481 (suppressed)  
    }  
  
    return 0;  
}  
```  
  
 Cet exemple illustre quelques-uns des avertissements que les C++ règles de contrôle de base peuvent trouver :  
  
- C26494 est de type règle. 5 : Initialise toujours un objet.  
  
- C26485 est une limite de règle. 3 : aucune atténuation de tableau à pointeur.  
  
- C26481 est une limite de règle. 1 : n’utilisez pas l’arithmétique de pointeur. Utilisez plutôt `span` .  
  
  Si les C++ ensembles de règles d’analyse du code de contrôle de base sont installés et activés lorsque vous compilez ce code, les deux premiers avertissements sont générés, mais le troisième est supprimé. Voici la sortie de la génération de l’exemple de code :  
  
**1 >------Build démarrée : projet : CoreCheckExample, configuration : déboguer Win32--**  
**----**  
**1 > CoreCheckExample. cpp**  
**1 > CoreCheckExample. vcxproj-> C:\Users\username\documents\visual Studio 2015 \ P**  
**rojects\CoreCheckExample\Debug\CoreCheckExample.exe**  
**1 > CoreCheckExample. vcxproj-> C:\Users\username\documents\visual Studio 2015 \ P**  
**rojects\CoreCheckExample\Debug\CoreCheckExample.pdb (fichier PDB complet)**  
**c:\Users\Username\Documents\Visual Studio 2015 \ projects\corecheckexample\coreche**  
**ckexample\corecheckexample.cpp (6) : avertissement C26494 : la variable’arr’est Uninitialize**  
**Ed. Initialisez toujours un objet. (type. 5 : https://go.microsoft.com/fwlink/p/?Link**  
**ID=620421)**  
**c:\Users\Username\Documents\Visual Studio 2015 \ projects\corecheckexample\coreche**  
**ckexample\corecheckexample.cpp (7) : avertissement C26485 : expression’arr' : aucun tableau à**  
**atténuation du pointeur. (Bounds. 3 : https://go.microsoft.com/fwlink/p/?LinkID=620415)**  
= = = = = = = = = = **Build : 1 a réussi, 0 a échoué, 0 a été mis à jour, 0 a été ignoré = =** = = = = = = = = = Les C++ recommandations de base sont là pour vous aider à écrire du code plus sécurisé. Toutefois, si vous avez une instance dans laquelle une règle ou un profil ne doit pas être appliqué, il est facile de la supprimer directement dans le code. Vous pouvez utiliser l’attribut `gsl::suppress` pour garder C++ le contrôle principal de la détection et du signalement d’une violation d’une règle dans le bloc de code suivant. Vous pouvez marquer des instructions individuelles pour supprimer des règles spécifiques. Vous pouvez même supprimer le profil de limites entier en écrivant `[[gsl::suppress(bounds)]]` sans inclure un numéro de règle spécifique.  
  
## <a name="use-the-guideline-support-library"></a>Utiliser la bibliothèque de prise en charge des instructions  
 Le package NuGet Microsoft. CppCoreCheck installe également un package qui contient l’implémentation Microsoft de la bibliothèque de prise en charge des instructions (GSL). Le portail GSL est également disponible sous forme autonome à [http://www.nuget.org/packages/Microsoft.Gsl](https://www.nuget.org/packages/Microsoft.Gsl). Cette bibliothèque est utile si vous souhaitez suivre les instructions principales. Le portail GSL comprend des définitions qui vous permettent de remplacer des constructions sujettes aux erreurs par des alternatives plus sûres. Par exemple, vous pouvez remplacer une paire `T*, length` de paramètres par le type `span<T>`. Le portail GSL est open source. par conséquent, si vous souhaitez consulter les sources de bibliothèque, commenter ou contribuer, le projet se trouve sur [https://github.com/Microsoft/GSL](https://github.com/Microsoft/GSL).
