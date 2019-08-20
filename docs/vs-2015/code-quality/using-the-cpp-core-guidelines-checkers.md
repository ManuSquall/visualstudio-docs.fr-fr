---
title: À l’aide du C++ Core Guidelines checkers | Microsoft Docs
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.date: 11/15/2016
ms.topic: conceptual
ms.assetid: a2098fd9-8334-4e95-9b8d-bc3da689d9e3
caps.latest.revision: 11
author: mikeblome
ms.author: mblome
manager: jillfra
ms.openlocfilehash: c0fb306cb7326464af847f09b319e8e702c76831
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68142089"
---
# <a name="using-the-c-core-guidelines-checkers"></a>Utilisation des vérificateurs C++ Core Guidelines
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Les recommandations C++ Core Guidelines sont un ensemble portable d’instructions, des règles et des meilleures pratiques sur le codage en C++ créé par les concepteurs et les experts de C++.  Visual Studio prend désormais en charge les packages de-créer des règles supplémentaires pour le code des outils d’analyse pour vérifier la conformité avec les recommandations C++ Core Guidelines dans votre code et de suggérer des améliorations.  
  
## <a name="the-c-core-guidelines-project"></a>Les recommandations C++ Core Guidelines de projet  
 Créé par Bjarne Stroustrup et d’autres, les recommandations C++ Core Guidelines sont un guide d’utilisation de C++ moderne efficacement et en toute sécurité. Les instructions de mettre l’accent sur la sécurité de type statique et sécurité des ressources. Ils identifient les moyens pour éliminer ou réduire les parties plus sujet aux erreurs de la langue et que vous suggèrent comment rendre votre code plus simple et plus performant de façon fiable. Ces instructions sont gérées par le Standard C++ Foundation. Pour plus d’informations, consultez la documentation, [C++ Core Guidelines](http://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines)et accéder aux fichiers de projet de documentation de C++ Core Guidelines sur [GitHub](https://github.com/isocpp/CppCoreGuidelines).  
  
 Microsoft prend en charge les efforts de C++ Core Guidelines en rendant C++ Core Check des ensembles de règles d’analyse de code que vous pouvez ajouter à vos projets à l’aide d’un package Nuget. Le package est nommé Microsoft.CppCoreCheck, et il est disponible à l’adresse [ http://www.nuget.org/packages/Microsoft.CppCoreCheck ](http://www.nuget.org/packages/Microsoft.CppCoreCheck). Ce package nécessite que vous avez au moins installé Visual Studio 2015 avec Update 1.  
  
 Le package installe également un autre package en tant que dépendance, un en-tête seule orientation prise en charge de bibliothèque (GSL). GSL est également disponible sur GitHub à l’adresse [ https://github.com/Microsoft/GSL ](https://github.com/Microsoft/GSL).  
  
## <a name="enable-the-c-core-check-guidelines-in-code-analysis"></a>Activer les recommandations C++ Core Check dans l’analyse du Code  
 Pour activer les outils d’analyse du code C++ Core Check, installez le package NuGet de Microsoft.CppCoreCheck dans chaque projet C++ que vous souhaitez vérifier dans Visual Studio.  
  
#### <a name="to-add-the-microsoftcppcorecheck-package-to-your-project"></a>Pour ajouter le package de Microsoft.CppCoreCheck à votre projet  
  
1. Dans **l’Explorateur de solutions**, avec le bouton droit pour ouvrir le menu contextuel de votre projet dans la Solution que vous souhaitez ajouter le package. Choisissez **gérer les Packages NuGet** pour ouvrir le **Gestionnaire de Package NuGet**.  
  
2. Dans le **Gestionnaire de Package NuGet** fenêtre, recherchez Microsoft.CppCoreCheck.  
  
    ![Fenêtre du Gestionnaire de Package NuGet montre CppCoreCheck package](../code-quality/media/cppcorecheck-nuget-window.PNG "CPPCoreCheck_Nuget_Window")  
  
3. Sélectionnez le package Microsoft.CppCoreCheck, puis choisissez le **installer** pour ajouter les règles à votre projet.  
  
   Le package NuGet ajoute un fichier .targets de MSBuild supplémentaire à votre projet qui est appelé lorsque vous activez l’analyse du code dans votre projet. Ce fichier .targets ajoute les règles C++ Core Check comme une extension supplémentaire à l’outil d’analyse de code Visual Studio.  
  
   Vous pouvez activer l’analyse du code sur votre projet en sélectionnant le **activer l’analyse du Code sur la Build** case à cocher dans la **analyse du Code** section de la **Pages de propriétés** boîte de dialogue pour votre projet.  
  
   ![Page de propriétés de paramètres généraux d’analyse de Code](../code-quality/media/cppcorecheck-codeanalysis-general.png "CPPCoreCheck_CodeAnalysis_General")  
  
   Les règles C++ Core Check font partie des ensembles de règles par défaut qui s’exécutent lors de l’analyse du code est activée. Étant donné que les règles C++ Core Check sont en cours de développement, certaines règles peuvent ne pas être prêt à être utilisé sur tout le code, mais peuvent être informatives pendant le développement. Ces règles sont publiées comme expérimentale. Vous pouvez choisir d’exécuter les règles a été résiliés ou expérimentales dans les propriétés de votre projet.  
  
   ![Page de propriétés pour les paramètres de Code Analysis Extensions](../code-quality/media/cppcorecheck-codeanalysis-extensions.png "CPPCoreCheck_CodeAnalysis_Extensions")  
  
   Pour activer ou désactiver les ensembles de règles C++ Core Check, ouvrez le **Pages de propriétés** boîte de dialogue pour votre projet. Sous **propriétés de Configuration**, développez **analyse du Code**, **Extensions**. Dans la liste déroulante contrôler regard **activer C++ Core Check (Released)** ou **activer C++ Core Check (expérimental)** , choisissez **Oui** ou **non**. Choisissez **OK** ou **appliquer** pour enregistrer vos modifications.  
  
## <a name="check-types-bounds-and-lifetimes"></a>Vérifiez les Types, les limites et les durées de vie  
 Le package C++ Core Check contient actuellement des vérificateurs pour le [sécurité de Type](http://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines#SS-type), [délimite sécurité](http://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines#SS-bounds), et [sécurité de la durée de vie](http://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines#SS-lifetime) profils.  
  
 Voici un exemple du genre de problèmes que les règles C++ Core Check trouverez :  
  
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
  
 Cet exemple illustre quelques-unes des avertissements que les règles C++ Core Check trouverez :  
  
- C26494 est règle Type.5 : Initialisez toujours un objet.  
  
- C26485 est règle Bounds.3 : Aucune perte de tableau en pointeur.  
  
- C26481 est règle Bounds.1 : N’utilisez pas opérations arithmétiques de pointeur. Utilisez plutôt `span`.  
  
  Si les ensembles de règles C++ Core Check l’analyse de code sont installées et activées lorsque vous compilez ce code, les deux premiers avertissements sont générés, mais la troisième est supprimée. Voici la sortie de génération à partir de l’exemple de code :  
  
  **1 >---début de la génération : Projet : CoreCheckExample, Configuration : Débogage Win32--**  
**----**  
**1 > CoreCheckExample.cpp**  
**1 > CoreCheckExample.vcxproj -> C:\Users\username\documents\visual studio 2015\P**  
**rojects\CoreCheckExample\Debug\CoreCheckExample.exe**  
**1 > CoreCheckExample.vcxproj -> C:\Users\username\documents\visual studio 2015\P**  
**rojects\CoreCheckExample\Debug\CoreCheckExample.pdb (fichier PDB complet)**  
**c:\users\username\documents\visual studio 2015\projects\corecheckexample\coreche**  
**ckexample\corecheckexample.cpp(6) : avertissement C26494 : La variable « arr » est uninitializ**  
**Ed. initialisez toujours un objet. (type.5 : http://go.microsoft.com/fwlink/p/?Link**  
**ID=620421)**  
**c:\users\username\documents\visual studio 2015\projects\corecheckexample\coreche**  
**ckexample\corecheckexample.cpp(7) : avertissement C26485 : Expression « arr » : Aucun tableau à**  
 **atténuation de pointeur. (bounds.3 : http://go.microsoft.com/fwlink/p/?LinkID=620415)**  
**=== Build : 1 a réussi, 0 a échoué, 0 mis à jour, 0 a été ignoré ===** The C++ Core Guidelines sont là pour vous aider à écrire du code de meilleure et plus sûr. Toutefois, si vous avez une instance où une règle ou un profil ne doit pas être appliqué, il est facile de supprimer directement dans le code. Vous pouvez utiliser le `gsl::suppress` attribut conserver C++ Core Check de détection et de signaler toute violation d’une règle dans le bloc de code suivant. Vous pouvez marquer les instructions individuelles pour supprimer des règles spécifiques. Vous pouvez même supprimer le profil bounds entière en écrivant `[[gsl::suppress(bounds)]]` sans inclure un numéro de règle spécifique.  
  
## <a name="use-the-guideline-support-library"></a>Utiliser la bibliothèque de prise en charge d’indication  
 Le package NuGet de Microsoft.CppCoreCheck installe également un package qui contient l’implémentation Microsoft de la bibliothèque de prise en charge d’orientation (GSL). GSL est également disponible dans leur forme autonome à [ http://www.nuget.org/packages/Microsoft.Gsl ](http://www.nuget.org/packages/Microsoft.Gsl). Cette bibliothèque est utile si vous souhaitez suivre les instructions de base. GSL inclut les définitions qui vous permettent de remplacer des constructions susceptibles d’engendrer des erreurs avec des solutions plus sûres. Par exemple, vous pouvez remplacer un `T*, length` paire de paramètres avec le `span<T>` type. GSL étant open source, si vous souhaitez jeter un coup de œil à la source de la bibliothèque, commentaire ou contribuer, le projet, consultez [ https://github.com/Microsoft/GSL ](https://github.com/Microsoft/GSL).
