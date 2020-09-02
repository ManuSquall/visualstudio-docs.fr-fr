---
title: Utilisation de Microsoft.VisualStudio.TestTools.CppUnitTestFramework | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: d1ac9188-d79f-407e-9f3a-80dbefa66317
caps.latest.revision: 10
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c561555df40bc02c3c9f3090ee1de4c0f329bcdc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72657171"
---
# <a name="using-microsoftvisualstudiotesttoolscppunittestframework"></a>Utilisation de Microsoft.VisualStudio.TestTools.CppUnitTestFramework
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Cette rubrique liste les membres publics de l’espace de noms `Microsoft::VisualStudio::CppUnitTestFramework`.

 Les fichiers d’en-tête se trouvent dans le dossier _dossier dossierinstallationvisualstudio2012 [x86] InstallFolder_**\VC\UnitTest\include**

 Les fichiers lib se trouvent dans le dossier _dossier dossierinstallationvisualstudio2012 [x86] InstallFolder_**\VC\UnitTest\lib**

## <a name="in-this-topic"></a><a name="BKMK_In_this_topic"></a> Dans cette rubrique
 [CppUnitTest. h](#BKMK_CppUnitTest_h)

- [Créer des classes et des méthodes de test](#BKMK_Create_test_classes_and_methods)

- [Initialiser et nettoyer](#BKMK_Initialize_and_cleanup)

  - [Méthodes de test](#BKMK_Test_methods)

  - [Classes de test](#BKMK_Test_classes)

  - [Modules de test](#BKMK_Test_modules)

- [Créer des attributs de test](#BKMK_Create_test_attributes)

  - [Attributs de méthode de test](#BKMK_Test_method_attributes)

  - [Attributs de classe de test](#BKMK_Test_class_attributes)

  - [Attributs de module de test](#BKMK_Test_module_attributes)

  - [Attributs prédéfinis](#BKMK_Pre_defined_attributes)

    [CppUnitTestAssert.h](#BKMK_CppUnitTestAssert_h)

  - [Assertions générales](#BKMK_General_Asserts)

    - [Sont égaux](#BKMK_General_Are_Equal)

    - [Ne sont pas égaux](#BKMK_General_Are_Not_Equal)

    - [Sont identiques](#BKMK_General_Are_Same)

    - [Ne sont pas identiques](#BKMK_General_Are_Not_Same)

    - [Est null](#BKMK_General_Is_Null)

    - [N’est pas null](#BKMK_General_Is_Not_Null)

    - [A la valeur true](#BKMK_General_Is_True)

    - [A la valeur false](#BKMK_General_Is_False)

    - [Échec](#BKMK_General_Fail)

  - [Assertions de Windows Runtime](#BKMK_WinRT_Asserts)

    - [Sont égaux](#BKMK_WinRT_Are_Equal)

    - [Sont identiques](#BKMK_WinRT_Are_Same)

    - [Ne sont pas égaux](#BKMK_WinRT_Are_Not_Equal)

    - [Ne sont pas identiques](#BKMK_WinRT_Are_Not_Same)

    - [Est null](#BKMK_WinRT_Is_Null)

    - [N’est pas null](#BKMK_WinRT_Is_Not_Null)

  - [Assertions d’exception](#BKMK_Exception_Asserts)

    - [S’attendre à une exception](#BKMK_Expect_Exception)

      [CppUnitTestLogger.h](#BKMK_CppUnitTestLogger_h)

    - [Enregistreur](#BKMK_Logger)

    - [Écrire un message](#BKMK_Write_Message)

## <a name="cppunittesth"></a><a name="BKMK_CppUnitTest_h"></a> CppUnitTest.h

### <a name="create-test-classes-and-methods"></a><a name="BKMK_Create_test_classes_and_methods"></a> Créer des classes et des méthodes de test

```cpp
TEST_CLASS(className)
```

 Obligatoire pour chaque classe contenant des méthodes de test. Identifie *className* en tant que classe de test. `TEST_CLASS` doit être déclaré dans la portée d’espace de noms.

```cpp
TEST_METHOD(methodName)
{
    // test method body
}

```

 Définit *methodName* en tant que méthode de test. `TEST_METHOD` doit être déclaré dans la portée de la classe de la méthode.

### <a name="initialize-and-cleanup"></a><a name="BKMK_Initialize_and_cleanup"></a> Initialiser et nettoyer

#### <a name="test-methods"></a><a name="BKMK_Test_methods"></a> Méthodes de test

```cpp
TEST_METHOD_INITIALIZE(methodName)
{
    // method initialization code
}

```

 Définit *methodName* en tant que méthode qui s’exécute avant l’exécution de chaque méthode de test. `TEST_METHOD_INITIALIZE` ne peut être défini qu’une seule fois dans une classe de test et doit être défini dans la classe de test.

```cpp
TEST_METHOD_CLEANUP(methodName)
{
    // test method cleanup  code
}

```

 Définit *methodName* en tant que méthode qui s’exécute après l’exécution de chaque méthode de test. `TEST_METHOD_CLEANUP` ne peut être défini qu’une seule fois dans une classe de test et doit être défini dans la portée de la classe de test.

#### <a name="test-classes"></a><a name="BKMK_Test_classes"></a> Classes de test

```cpp
TEST_CLASS_INITIALIZE(methodName)
{
    // test class initialization  code
}

```

 Définit *methodName* en tant que méthode qui s’exécute après la création de chaque classe de test. `TEST_CLASS_INITIALIZE` ne peut être défini qu’une seule fois dans une classe de test et doit être défini dans la portée de la classe de test.

```cpp
TEST_CLASS_CLEANUP(methodName)
{
    // test class cleanup  code
}

```

 Définit *methodName* en tant que méthode qui s’exécute après la création de chaque classe de test. `TEST_CLASS_CLEANUP` ne peut être défini qu’une seule fois dans une classe de test et doit être défini dans la portée de la classe de test.

#### <a name="test-modules"></a><a name="BKMK_Test_modules"></a> Modules de test

```cpp
TEST_MODULE_INITIALIZE(methodName)
{
    // module initialization code
}
```

 Définit la méthode *methodName* qui s’exécute au moment du chargement d’un module. `TEST_MODULE_INITIALIZE` ne peut être défini qu’une seule fois dans un module de test et doit être déclaré dans la portée de l’espace de noms.

```cpp
TEST_MODULE_CLEANUP(methodName)
```

 Définit la méthode *methodName* qui s’exécute au moment du déchargement d’un module. `TEST_MODULE_CLEANUP` ne peut être défini qu’une seule fois dans un module de test et doit être déclaré dans la portée de l’espace de noms.

### <a name="create-test-attributes"></a><a name="BKMK_Create_test_attributes"></a> Créer des attributs de test

#### <a name="test-method-attributes"></a><a name="BKMK_Test_method_attributes"></a> Attributs de méthode de test

```cpp
BEGIN_TEST_METHOD_ATTRIBUTE(testMethodName)
    TEST_METHOD_ATTRIBUTE(attributeName, attributeValue)
    ...
END_TEST_METHOD_ATTRIBUTE()
```

 Ajoute les attributs définis avec une ou plusieurs macros `TEST_METHOD_ATTRIBUTE` à la méthode de test *testClassName*.

 Une macro `TEST_METHOD_ATTRIBUTE` définit un attribut avec le nom *attributeName* et la valeur *attributeValue*.

#### <a name="test-class-attributes"></a><a name="BKMK_Test_class_attributes"></a> Attributs de la classe de test

```cpp
BEGIN_TEST_CLASS_ATTRIBUTE(testClassName)
    TEST_CLASS_ATTRIBUTE(attributeName, attributeValue)
    ...
END_TEST_CLASS_ATTRIBUTE()
```

 Ajoute les attributs définis avec une ou plusieurs macros `TEST_CLASS_ATTRIBUTE` à la classe de test *testClassName*.

 Une macro `TEST_CLASS_ATTRIBUTE` définit un attribut avec le nom *attributeName* et la valeur *attributeValue*.

#### <a name="test-module-attributes"></a><a name="BKMK_Test_module_attributes"></a> Attributs du module de test

```cpp
BEGIN_TEST_MODULE_ATTRIBUTE(testModuleName)
    TEST_MODULE_ATTRIBUTE(attributeName, attributeValue)
    ...
END_TEST_MODULE_ATTRIBUTE()
```

 Ajoute les attributs définis avec une ou plusieurs macros `TEST_MODULE_ATTRIBUTE` au module de test *testModuleName*.

 Une macro `TEST_MODULE_ATTRIBUTE` définit un attribut avec le nom *attributeName* et la valeur *attributeValue*.

#### <a name="pre-defined-attributes"></a><a name="BKMK_Pre_defined_attributes"></a> Attributs prédéfinis
 Ces macros d’attributs prédéfinis peuvent être remplacées par les macros `TEST_METHOD_ATTRIBUTE`, `TEST_CLASS_ATTRIBUTE` ou `TEST_MODULE_ATTRIBUTE` décrites ci-dessus.

```cpp
TEST_OWNER(ownerAlias)
```

 Définit un attribut avec le nom `Owner` et la valeur d’attribut *ownerAlias*.

```cpp
TEST_DESCRIPTION(description)
```

 Définit un attribut avec le nom `Description` et la valeur d’attribut *description*.

```cpp
TEST_PRIORITY(priority)
```

 Définit un attribut avec le nom `Priority` et la valeur d’attribut *priority*.

```cpp
TEST_WORKITEM(workitem)
```

 Définit un attribut avec le nom `WorkItem` et la valeur d’attribut *workItem*.

```cpp
TEST_IGNORE()
```

 Définit un attribut avec le nom `Ignore` et la valeur d’attribut `true`.

## <a name="cppunittestasserth"></a><a name="BKMK_CppUnitTestAssert_h"></a> CppUnitTestAssert. h

### <a name="general-asserts"></a><a name="BKMK_General_Asserts"></a> Assertions générales

#### <a name="are-equal"></a><a name="BKMK_General_Are_Equal"></a> Sont égaux
 Vérifie que deux objets sont égaux

```cpp
template<typename T>
static void AreEqual(
    const T& expected,
    const T& actual,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

 Vérifie que deux valeurs double sont égales

```cpp
static void AreEqual(
    double expected,
    double actual,
    double tolerance,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

 Vérifie que deux valeurs float sont égales

```cpp
static void AreEqual(
    float expected,
    float actual,
    float tolerance,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

 Vérifie que deux chaînes char* sont égales

```cpp
static void AreEqual(
    const char* expected,
    const char* actual,
    bool ignoreCase = false,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

 Vérifie que deux chaînes w_char* sont égales

```cpp
static void AreEqual(
    const wchar_t* expected,
    const wchar_t* actual,
    bool ignoreCase = false,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

#### <a name="are-not-equal"></a><a name="BKMK_General_Are_Not_Equal"></a> Ne sont pas égaux
 Vérifie que deux valeurs double ne sont pas égales

```cpp
static void AreNotEqual(
    double notExpected,
    double actual,
    double tolerance,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

 Vérifie que deux valeurs float ne sont pas égales

```cpp
static void AreNotEqual(
    float notExpected,
    float actual,
    float tolerance,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

 Vérifie que deux chaînes char* ne sont pas égales

```cpp
static void AreNotEqual(
    const char* notExpected,
    const char* actual,
    bool ignoreCase = false,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

 Vérifie que deux chaînes w_char* ne sont pas égales

```cpp
static void AreNotEqual(
    const wchar_t* notExpected,
    const wchar_t* actual,
    bool ignoreCase = false,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

 Vérifie que deux références ne sont pas égales sur la base de l’opérateur ==.

```cpp
template<typename T>
static void AreNotEqual(
    const T& notExpected,
    const T& actual,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

#### <a name="are-same"></a><a name="BKMK_General_Are_Same"></a> Sont identiques
 Vérifie que deux références référencent la même instance d’objet (identité).

```cpp
template<typename T>
static void AreSame(
    const T& expected,
    const T& actual,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

#### <a name="are-not-same"></a><a name="BKMK_General_Are_Not_Same"></a> Ne sont pas identiques
 Vérifie que deux références ne référencent pas la même instance d’objet (identité).

```cpp
template<typename T>
static void AreNotSame (
    const T& notExpected,
    const T& actual,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

#### <a name="is-null"></a><a name="BKMK_General_Is_Null"></a> Est null
 Vérifie qu’un pointeur a une valeur NULL.

```cpp
template<typename T>
static void IsNull(
    const T* actual,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

#### <a name="is-not-null"></a><a name="BKMK_General_Is_Not_Null"></a> N’est pas null
 Vérifie qu’un pointeur n’a pas une valeur NULL

```cpp
template<typename T>
static void IsNotNull(
    const T* actual,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

#### <a name="is-true"></a><a name="BKMK_General_Is_True"></a> A la valeur true
 Vérifie qu’une condition est vraie

```cpp
static void IsTrue(
    bool condition,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

#### <a name="is-false"></a><a name="BKMK_General_Is_False"></a> A la valeur false
 Vérifie qu’une condition est fausse

```cpp
static void IsFalse(
    bool condition,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

#### <a name="fail"></a><a name="BKMK_General_Fail"></a> Incident
 Force l’échec du résultat du cas de test

```cpp
static void Fail(
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

### <a name="windows-runtime-asserts"></a><a name="BKMK_WinRT_Asserts"></a> Assertions Windows Runtime

#### <a name="are-equal"></a><a name="BKMK_WinRT_Are_Equal"></a> Sont égaux
 Vérifie que deux pointeurs Windows Runtime sont égaux.

```
template<typename T>
static void AreEqual(
    T^ expected,
    T^ actual,
    Platform::String^ message = nullptr,
    const __LineInfo* pLineInfo= nullptr)
```

 Vérifie que deux chaînes Platform::String^ sont égales.

```
template<typename T>
static void AreEqual(
    T^ expected,
    T^ actual,
    Platform::String^ message= nullptr,
    const __LineInfo* pLineInfo= nullptr)
```

#### <a name="are-same"></a><a name="BKMK_WinRT_Are_Same"></a> Sont identiques
 Vérifie que deux références Windows Runtime référencent le même objet.

```
template<typename T>
static void AreSame(
    T% expected,
    T% actual,
    Platform::String^ message= nullptr,
    const __LineInfo* pLineInfo= nullptr)
```

#### <a name="are-not-equal"></a><a name="BKMK_WinRT_Are_Not_Equal"></a> Ne sont pas égaux
 Vérifie que deux pointeurs Windows Runtime ne sont pas égaux.

```
template<typename T>
static void AreNotEqual(
    T^ notExpected,
    T^ actual,
    Platform::String^ message = nullptr,
    const __LineInfo* pLineInfo= nullptr)
```

 Vérifie que deux chaînes Platform::String^ ne sont pas égales.

```
static void AreNotEqual(
    Platform::String^ notExpected,
    Platform::String^ actual,
    bool ignoreCase = false,
    Platform::String^ message= nullptr,
    const __LineInfo* pLineInfo= nullptr)
```

#### <a name="are-not-same"></a><a name="BKMK_WinRT_Are_Not_Same"></a> Ne sont pas identiques
 Vérifie que deux références Windows Runtime ne référencent pas le même objet.

```
template<typename T>
static void AreNotSame(
    T% notExpected,
    T% actual,
    Platform::String^ message= nullptr,
    const __LineInfo* pLineInfo= nullptr)
```

#### <a name="is-null"></a><a name="BKMK_WinRT_Is_Null"></a> Est null
 Vérifie qu’un pointeur Windows Runtime est nullptr.

```
template<typename T>
static void IsNull(
    T^ actual,
    Platform::String^ message = nullptr,
    const __LineInfo* pLineInfo= nullptr)
```

#### <a name="is-not-null"></a><a name="BKMK_WinRT_Is_Not_Null"></a> N’est pas null
 Vérifie qu’un pointeur Windows Runtime n’est pas nullptr.

```
template<typename T>
static void IsNotNull(
    T^ actual,
    Platform::String^ message= nullptr,
    const __LineInfo* pLineInfo= nullptr)
```

### <a name="exception-asserts"></a><a name="BKMK_Exception_Asserts"></a> Assertions d’exception

#### <a name="expect-exception"></a><a name="BKMK_Expect_Exception"></a> Exception attendue
 Vérifie qu’une fonction lève une exception :

```
template<typename _EXPECTEDEXCEPTION, typename _FUNCTOR>
static void ExpectException(
    _FUNCTOR functor,
    const wchar_t* message= NULL,
    const __LineInfo* pLineInfo= NULL)
```

 Vérifie qu’une fonction lève une exception :

```
template<typename _EXPECTEDEXCEPTION, typename _RETURNTYPE>
    static void ExpectException(
    _RETURNTYPE (*func)(),
    const wchar_t* message= NULL,
    const __LineInfo* pLineInfo = NULL)
```

## <a name="cppunittestloggerh"></a><a name="BKMK_CppUnitTestLogger_h"></a> CppUnitTestLogger. h

### <a name="logger"></a><a name="BKMK_Logger"></a> Suivi
 La classe de journalisation contient des méthodes statiques où écrire

```
class Logger
```

### <a name="write-message"></a><a name="BKMK_Write_Message"></a> Écrire un message

```
static void
Logger::WriteMessage(const wchar_t* message)
```

```
static void
Logger::WriteMessage(const char* message)
```

## <a name="example"></a>Exemple
 Ce code est un exemple de

```
////////////////////////////////////////////////////////////
/* USAGE EXAMPLE
// The following is an example of VSCppUnit usage.
// It includes examples of attribute metadata, fixtures,
// unit tests with assertions, and custom logging.

#include <CppUnitTest.h>

using namespace Microsoft::VisualStudio::CppUnitTestFramework;

BEGIN_TEST_MODULE_ATTRIBUTE()
    TEST_MODULE_ATTRIBUTE(L"Date", L"2010/6/12")
END_TEST_MODULE_ATTRIBUTE()

TEST_MODULE_INITIALIZE(ModuleInitialize)
{
    Logger::WriteMessage("In Module Initialize");
}

TEST_MODULE_CLEANUP(ModuleCleanup)
{
    Logger::WriteMessage("In Module Cleanup");
}

TEST_CLASS(Class1)
{

public:

    Class1()
    {
        Logger::WriteMessage("In Class1");
    }

    ~Class1()
    {
        Logger::WriteMessage("In ~Class1");
    }

    TEST_CLASS_INITIALIZE(ClassInitialize)
    {
        Logger::WriteMessage("In Class Initialize");
    }

    TEST_CLASS_CLEANUP(ClassCleanup)
    {
        Logger::WriteMessage("In Class Cleanup");
    }

    BEGIN_TEST_METHOD_ATTRIBUTE(Method1)
        TEST_OWNER(L"OwnerName")
        TEST_PRIORITY(1)
    END_TEST_METHOD_ATTRIBUTE()

    TEST_METHOD(Method1)
    {
        Logger::WriteMessage("In Method1");
        Assert::AreEqual(0, 0);
    }

    TEST_METHOD(Method2)
    {
        Assert::Fail(L"Fail");
    }
};
```

## <a name="see-also"></a>Voir aussi
 [Test unitaire de vos](../test/unit-test-your-code.md) [tests unitaires de code code natif avec l’Explorateur de tests](https://msdn.microsoft.com/8a09d6d8-3613-49d8-9ffe-11375ac4736c) [Ajout de tests unitaires à des applications C++ existantes](../test/unit-testing-existing-cpp-applications-with-test-explorer.md)
