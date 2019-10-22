---
title: Exemples de développement mobile multiplateforme | Microsoft Docs
ms.custom: ''
ms.date: 10/17/2019
ms.technology: vs-ide-mobile
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: bc384c12-fccc-45d7-9fb9-b90d536aa663
author: corob-msft
ms.author: corob
manager: jillfra
ms.workload:
- xplat-cplusplus
ms.openlocfilehash: 31619757684811fb5090e6edb05c464be59fa4dd
ms.sourcegitcommit: 8a96a65676fd7a2a03b0803d7eceae65f3fa142b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72589001"
---
# <a name="cross-platform-mobile-development-examples"></a>Exemples de développement mobile multiplateforme

Plusieurs des modèles installés par le **développement mobile avec une C++**  charge de travail génèrent des exemples complets que vous pouvez utiliser pour vous familiariser avec. En outre, le Centre de développement Windows présente plusieurs exemples d’applications que vous pouvez télécharger et essayer dans Visual Studio.

- [Exemple d’application Android hello-jni](https://code.msdn.microsoft.com/hello-jni-Android-790ab73d)

   Cet exemple fait partie de l’application hello-jni du Kit de développement natif (NDK) Android. L’exemple illustre une application « Hello World » JNI (Java Native Interface) de bout en bout. Il charge une chaîne à partir d’une méthode native implémentée dans une bibliothèque partagée, puis l’affiche dans l’application.

- [Exemple d’application Android hello-gl2](https://code.msdn.microsoft.com/hello-gl2-Android-3b61896c)

   Cet exemple fait partie de l’application hello-gl2 du Kit de développement natif (NDK) Android. L’exemple illustre une application Android OpenGL JNI (Java Native Interface) de bout en bout. Il affiche un triangle à l’aide des API du nuanceur OpenGL ES 2.0.

- [Exemple d’application Android Bitmap Plasma](https://code.msdn.microsoft.com/Bitmap-Plasma-Android-77ae296a)

   Cet exemple fait partie de l’application Bitmap Plasma du Kit de développement natif (NDK) Android. L’exemple illustre une application Android OpenGL ES 2.0 JNI (Java Native Interface) de bout en bout. Il illustre la manipulation directe des mémoires tampons de pixels de bitmaps Android pour générer un effet plasma.

- [Exemple de bibliothèque Android TwoLibs](https://code.msdn.microsoft.com/TwoLibs-Android-Library-6396e5c4)

   Cet exemple fait partie de l’exemple TwoLibs du Kit de développement natif (NDK) Android. Il utilise une bibliothèque partagée chargée dynamiquement et une bibliothèque native Android C++ statique qui implémente une méthode appelée à partir d’une application JNI (Java Native Interface). Cet exemple constitue un bon point de départ pour que les développeurs sachent comment utiliser des bibliothèques partagées statiques/dynamiques pour créer une application Android JNI de bout en bout avec Visual Studio.

- [Exemple d’application Android Tea Pot](https://code.msdn.microsoft.com/Tea-Pot-Android-Application-e7c05d73)

   Cet exemple fait partie de l’application TeaPot du Kit de développement natif (NDK) Android. L’exemple illustre une application Android OpenGL ES 2.0 JNI (Java Native Interface) de bout en bout.

- [Exemple d’application Android MoreTeaPots](https://code.msdn.microsoft.com/MoreTeaPots-Android-a9bd8549)

   Cet exemple fait partie de l’application MoreTeaPots du Kit de développement natif (NDK) Android. L’exemple illustre une application Android OpenGL JNI (Java Native Interface) de bout en bout.

- [Exemple de bibliothèque Android test-libstdcpp](https://code.msdn.microsoft.com/test-libstdcpp-Android-00b548f5)

   Cet exemple est un port de l’exemple de test-libstdc + + Android NDK, spécifiquement pour une utilisation avec Visual Studio. Cet exemple constitue un bon point de départ pour les développeurs pour apprendre à utiliser la bibliothèque standard.

  Pour ouvrir un des exemples dans Visual Studio, téléchargez le fichier zip et ouvrez la page **Propriétés** du fichier téléchargé dans l’explorateur. Choisissez le bouton **Débloquer** , puis **OK**. Extrayez le contenu du fichier zip vers un emplacement pratique, puis ouvrez le dossier C++ dans l’exemple extrait et ouvrez le fichier solution.

  Pour générer l’exemple, appuyez sur **F7** ou, dans la barre de menus, choisissez **Générer**, **Générer la solution**.