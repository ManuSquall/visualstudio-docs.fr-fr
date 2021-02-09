---
title: API Microsoft.VisualStudio.TestTools.CppUnitTestFramework
description: Cet article décrit les membres CppUnitTestFramework, que vous pouvez utiliser pour écrire des tests unitaires C++ basés sur l’infrastructure de test unitaire Native Microsoft.
ms.custom: SEO-VS-2020
ms.date: 09/27/2019
ms.topic: reference
ms.author: corob
manager: jmartens
ms.workload:
- multiple
author: corob-msft
ms.openlocfilehash: 355259f784d496fae574a331382d03d3fbe5bfd6
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99844526"
---
# <a name="microsoftvisualstudiotesttoolscppunittestframework-api-reference"></a>Informations de référence sur l’API Microsoft.VisualStudio.TestTools.CppUnitTestFramework

Cette rubrique liste les membres publics de l’espace de noms `Microsoft::VisualStudio::CppUnitTestFramework`. Utilisez ces API pour écrire des tests unitaires C++ basés sur le framework de tests unitaires natifs Microsoft. Vous pouvez trouver un [exemple d’utilisation](#example) à la fin de la rubrique.

Les fichiers d’en-tête et lib se trouvent sous *\<Visual Studio installation folder> \VC\Auxiliary\VS\UnitTest*.

Les chemins des fichiers d’en-tête et de bibliothèque sont configurés automatiquement dans un projet de test natif.

## <a name="in-this-topic"></a><a name="In_this_topic"></a> Dans cette rubrique

[CppUnitTest. h](#cppUnitTest_h)

- [Créer des classes et des méthodes de test](#create_test_classes_and_methods)

- [Initialiser et nettoyer](#Initialize_and_cleanup)

  - [Méthodes de test](#test_methods)

  - [Classes de test](#test_classes)

  - [Modules de test](#test_modules)

- [Créer des attributs de test](#create_test_attributes)

  - [Attributs de méthode de test](#test_method_attributes)

  - [Attributs de classe de test](#test_class_attributes)

  - [Attributs de module de test](#test_module_attributes)

  - [Attributs prédéfinis](#pre_defined_attributes)

    [CppUnitTestAssert.h](#cppUnitTestAssert_h)

  - [Assertions générales](#general_asserts)

    - [Sont égaux](#general_are_equal)

    - [Ne sont pas égaux](#general_are_not_equal)

    - [Sont identiques](#general_are_same)

    - [Ne sont pas identiques](#general_are_not_same)

    - [Est null](#general_is_null)

    - [N’est pas null](#general_is_not_null)

    - [A la valeur true](#general_is_True)

    - [A la valeur false](#general_is_false)

    - [Échec](#general_Fail)

  - [Assertions de Windows Runtime](#winrt_asserts)

    - [Sont égaux](#winrt_are_equal)

    - [Sont identiques](#winrt_are_same)

    - [Ne sont pas égaux](#winrt_are_not_equal)

    - [Ne sont pas identiques](#winrt_are_not_same)

    - [Est null](#winrt_is_null)

    - [N’est pas null](#winrt_is_not_null)

  - [Assertions d’exception](#exception_asserts)

    - [S’attendre à une exception](#expect_exception)

      [CppUnitTestLogger.h](#cppunittestlogger_h)

    - [Enregistreur](#logger)

    - [Écrire un message](#write_message)

  - [Exemple d’utilisation](#example)

## <a name="cppunittesth"></a><a name="cppUnitTest_h"></a> CppUnitTest.h

### <a name="create-test-classes-and-methods"></a><a name="create_test_classes_and_methods"></a> Créer des classes et des méthodes de test

```cpp
TEST_CLASS(className)
```

Obligatoire pour chaque classe contenant des méthodes de test. Identifie *className* en tant que classe de test. `TEST_CLASS` doit être déclaré dans la portée de l’espace de noms.

```cpp
TEST_METHOD(methodName)
{
    // test method body
}
```

Définit *methodName* en tant que méthode de test. `TEST_METHOD` doit être déclaré dans la portée de la classe de la méthode.

### <a name="initialize-and-cleanup"></a><a name="Initialize_and_cleanup"></a> Initialiser et nettoyer

#### <a name="test-methods"></a><a name="test_methods"></a> Méthodes de test

```cpp
TEST_METHOD_INITIALIZE(methodName)
{
    // method initialization code
}
```

Définit *methodName* en tant que méthode qui s’exécute avant l’exécution de chaque méthode de test. `TEST_METHOD_INITIALIZE` ne peut être défini qu’une seule fois dans une classe de test et doit être défini dans la portée de la classe de test.

```cpp
TEST_METHOD_CLEANUP(methodName)
{
    // test method cleanup  code
}
```

Définit *methodName* en tant que méthode qui s’exécute après l’exécution de chaque méthode de test. `TEST_METHOD_CLEANUP` ne peut être défini qu’une seule fois dans une classe de test et doit être défini dans la portée de la classe de test.

#### <a name="test-classes"></a><a name="test_classes"></a> Classes de test

```cpp
TEST_CLASS_INITIALIZE(methodName)
{
    // test class initialization  code
}
```

Définit *methodName* en tant que méthode qui s’exécute avant la création de chaque classe de test. `TEST_CLASS_INITIALIZE` ne peut être défini qu’une seule fois dans une classe de test et doit être défini dans la portée de la classe de test.

```cpp
TEST_CLASS_CLEANUP(methodName)
{
    // test class cleanup  code
}
```

Définit *methodName* en tant que méthode qui s’exécute après la création de chaque classe de test. `TEST_CLASS_CLEANUP` ne peut être défini qu’une seule fois dans une classe de test et doit être défini dans la portée de la classe de test.

#### <a name="test-modules"></a><a name="test_modules"></a> Modules de test

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

### <a name="create-test-attributes"></a><a name="create_test_attributes"></a> Créer des attributs de test

#### <a name="test-method-attributes"></a><a name="test_method_attributes"></a> Attributs de méthode de test

```cpp
BEGIN_TEST_METHOD_ATTRIBUTE(testMethodName)
    TEST_METHOD_ATTRIBUTE(attributeName, attributeValue)
    ...
END_TEST_METHOD_ATTRIBUTE()
```

Ajoute les attributs définis avec une ou plusieurs macros `TEST_METHOD_ATTRIBUTE` à la méthode de test *testMethodName*.

Une macro `TEST_METHOD_ATTRIBUTE` définit un attribut avec le nom *attributeName* et la valeur *attributeValue*.

#### <a name="test-class-attributes"></a><a name="test_class_attributes"></a> Attributs de la classe de test

```cpp
BEGIN_TEST_CLASS_ATTRIBUTE(testClassName)
    TEST_CLASS_ATTRIBUTE(attributeName, attributeValue)
    ...
END_TEST_CLASS_ATTRIBUTE()
```

Ajoute les attributs définis avec une ou plusieurs macros `TEST_CLASS_ATTRIBUTE` à la classe de test *testClassName*.

Une macro `TEST_CLASS_ATTRIBUTE` définit un attribut avec le nom *attributeName* et la valeur *attributeValue*.

#### <a name="test-module-attributes"></a><a name="test_module_attributes"></a> Attributs du module de test

```cpp
BEGIN_TEST_MODULE_ATTRIBUTE(testModuleName)
    TEST_MODULE_ATTRIBUTE(attributeName, attributeValue)
    ...
END_TEST_MODULE_ATTRIBUTE()
```

Ajoute les attributs définis avec une ou plusieurs macros `TEST_MODULE_ATTRIBUTE` au module de test *testModuleName*.

Une macro `TEST_MODULE_ATTRIBUTE` définit un attribut avec le nom *attributeName* et la valeur *attributeValue*.

#### <a name="pre-defined-attributes"></a><a name="pre_defined_attributes"></a> Attributs prédéfinis

Ces macros d’attributs prédéfinis sont fournis pour des raisons pratiques pour les cas courants. Ils peuvent être remplacées par la macro `TEST_METHOD_ATTRIBUTE` décrite ci-dessus.

```cpp
TEST_OWNER(ownerAlias)
```

Définit un `TEST_METHOD_ATTRIBUTE` avec le nom `Owner` et la valeur d’attribut *ownerAlias*.

```cpp
TEST_DESCRIPTION(description)
```

Définit un `TEST_METHOD_ATTRIBUTE` avec le nom `Description` et la valeur d’attribut *description*.

```cpp
TEST_PRIORITY(priority)
```

Définit un `TEST_METHOD_ATTRIBUTE` avec le nom `Priority` et la valeur de l’attribut *priority*.

```cpp
TEST_WORKITEM(workitem)
```

Définit un `TEST_METHOD_ATTRIBUTE` avec le nom `WorkItem` et la valeur de l’attribut *workItem*.

```cpp
TEST_IGNORE()
```

Définit un `TEST_METHOD_ATTRIBUTE` avec le nom `Ignore` et la valeur de l’attribut `true`.

## <a name="cppunittestasserth"></a><a name="cppUnitTestAssert_h"></a> CppUnitTestAssert. h

### <a name="general-asserts"></a><a name="general_asserts"></a> Assertions générales

#### <a name="are-equal"></a><a name="general_are_equal"></a> Sont égaux
Vérifie que deux objets sont égaux

```cpp
template<typename T>
static void Assert::AreEqual(
    const T& expected,
    const T& actual,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

Vérifie que deux valeurs double sont égales

```cpp
static void Assert::AreEqual(
    double expected,
    double actual,
    double tolerance,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

Vérifie que deux valeurs float sont égales

```cpp
static void Assert::AreEqual(
    float expected,
    float actual,
    float tolerance,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

Vérifie que deux chaînes char* sont égales

```cpp
static void Assert::AreEqual(
    const char* expected,
    const char* actual,
    bool ignoreCase = false,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

Vérifie que deux chaînes w_char* sont égales

```cpp
static void Assert::AreEqual(
    const wchar_t* expected,
    const wchar_t* actual,
    bool ignoreCase = false,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

#### <a name="are-not-equal"></a><a name="general_are_not_equal"></a> Ne sont pas égaux
Vérifie que deux valeurs double ne sont pas égales

```cpp
static void Assert::AreNotEqual(
    double notExpected,
    double actual,
    double tolerance,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

Vérifie que deux valeurs float ne sont pas égales

```cpp
static void Assert::AreNotEqual(
    float notExpected,
    float actual,
    float tolerance,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

Vérifie que deux chaînes char* ne sont pas égales

```cpp
static void Assert::AreNotEqual(
    const char* notExpected,
    const char* actual,
    bool ignoreCase = false,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

Vérifie que deux chaînes w_char* ne sont pas égales

```cpp
static void Assert::AreNotEqual(
    const wchar_t* notExpected,
    const wchar_t* actual,
    bool ignoreCase = false,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

Vérifie que deux références ne sont pas égales sur la base de l’opérateur ==.

```cpp
template<typename T>
static void Assert::AreNotEqual(
    const T& notExpected,
    const T& actual,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

#### <a name="are-same"></a><a name="general_are_same"></a> Sont identiques
Vérifie que deux références référencent la même instance d’objet (identité).

```cpp
template<typename T>
static void Assert::AreSame(
    const T& expected,
    const T& actual,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

#### <a name="are-not-same"></a><a name="general_are_not_same"></a> Ne sont pas identiques
Vérifie que deux références ne référencent pas la même instance d’objet (identité).

```cpp
template<typename T>
static void Assert::AreNotSame (
    const T& notExpected,
    const T& actual,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

#### <a name="is-null"></a><a name="general_is_null"></a> Est null
Vérifie qu’un pointeur a une valeur NULL.

```cpp
template<typename T>
static void Assert::IsNull(
    const T* actual,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

#### <a name="is-not-null"></a><a name="general_is_not_null"></a> N’est pas null
Vérifie qu’un pointeur n’a pas une valeur NULL

```cpp
template<typename T>
static void Assert::IsNotNull(
    const T* actual,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

#### <a name="is-true"></a><a name="general_is_True"></a> A la valeur true
Vérifie qu’une condition est vraie

```cpp
static void Assert::IsTrue(
    bool condition,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

#### <a name="is-false"></a><a name="general_is_false"></a> A la valeur false
Vérifie qu’une condition est fausse

```cpp
static void Assert::IsFalse(
    bool condition,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

#### <a name="fail"></a><a name="general_Fail"></a> Incident
Force l’échec du résultat du cas de test

```cpp
static void Assert::Fail(
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

### <a name="windows-runtime-asserts"></a><a name="winrt_asserts"></a> Assertions Windows Runtime

#### <a name="are-equal"></a><a name="winrt_are_equal"></a> Sont égaux
Vérifie que deux pointeurs Windows Runtime sont égaux.

```cpp
template<typename T>
static void Assert::AreEqual(
    T^ expected,
    T^ actual,
    Platform::String^ message = nullptr,
    const __LineInfo* pLineInfo= nullptr)
```

Vérifie que deux chaînes Platform::String^ sont égales.

```cpp
template<typename T>
static void Assert::AreEqual(
    T^ expected,
    T^ actual,
    Platform::String^ message= nullptr,
    const __LineInfo* pLineInfo= nullptr)
```

#### <a name="are-same"></a><a name="winrt_are_same"></a> Sont identiques
Vérifie que deux références Windows Runtime référencent le même objet.

```cpp
template<typename T>
static void Assert::AreSame(
    T% expected,
    T% actual,
    Platform::String^ message= nullptr,
    const __LineInfo* pLineInfo= nullptr)
```

#### <a name="are-not-equal"></a><a name="winrt_are_not_equal"></a> Ne sont pas égaux
Vérifie que deux pointeurs Windows Runtime ne sont pas égaux.

```cpp
template<typename T>
static void Assert::AreNotEqual(
    T^ notExpected,
    T^ actual,
    Platform::String^ message = nullptr,
    const __LineInfo* pLineInfo= nullptr)
```

Vérifie que deux chaînes Platform::String^ ne sont pas égales.

```cpp
static void Assert::AreNotEqual(
    Platform::String^ notExpected,
    Platform::String^ actual,
    bool ignoreCase = false,
    Platform::String^ message= nullptr,
    const __LineInfo* pLineInfo= nullptr)
```

#### <a name="are-not-same"></a><a name="winrt_are_not_same"></a> Ne sont pas identiques
Vérifie que deux références Windows Runtime ne référencent pas le même objet.

```cpp
template<typename T>
static void Assert::AreNotSame(
    T% notExpected,
    T% actual,
    Platform::String^ message= nullptr,
    const __LineInfo* pLineInfo= nullptr)
```

#### <a name="is-null"></a><a name="winrt_is_null"></a> Est null
Vérifie qu’un pointeur Windows Runtime est nullptr.

```cpp
template<typename T>
static void Assert::IsNull(
    T^ actual,
    Platform::String^ message = nullptr,
    const __LineInfo* pLineInfo= nullptr)
```

#### <a name="is-not-null"></a><a name="winrt_is_not_null"></a> N’est pas null
Vérifie qu’un pointeur Windows Runtime n’est pas nullptr.

```cpp
template<typename T>
static void Assert::IsNotNull(
    T^ actual,
    Platform::String^ message= nullptr,
    const __LineInfo* pLineInfo= nullptr)
```

### <a name="exception-asserts"></a><a name="exception_asserts"></a> Assertions d’exception

#### <a name="expect-exception"></a><a name="expect_exception"></a> Exception attendue
Vérifie qu’une fonction lève une exception :

```cpp
template<typename _EXPECTEDEXCEPTION, typename _FUNCTOR>
static void Assert::ExpectException(
    _FUNCTOR functor,
    const wchar_t* message= NULL,
    const __LineInfo* pLineInfo= NULL)
```

Vérifie qu’une fonction lève une exception :

```cpp
template<typename _EXPECTEDEXCEPTION, typename _RETURNTYPE>
    static void Assert::ExpectException(
    _RETURNTYPE (*func)(),
    const wchar_t* message= NULL,
    const __LineInfo* pLineInfo = NULL)
```

## <a name="cppunittestloggerh"></a><a name="cppunittestlogger_h"></a> CppUnitTestLogger. h

### <a name="logger"></a><a name="logger"></a> Suivi
La classe Logger contient des méthodes statiques pour écrire dans la **fenêtre Sortie**.

### <a name="write-message"></a><a name="write_message"></a> Écrire un message
Écrire une chaîne dans la **fenêtre Sortie**

```cpp
static void Logger::WriteMessage(const wchar_t* message)
```

```cpp
static void Logger::WriteMessage(const char* message)
```

## <a name="example"></a><a name="example"></a> Exemple
Ce code est un exemple d’utilisation de VSCppUnit. Il inclut des exemples de métadonnées d’attribut, de fixtures, de tests unitaires avec des assertions et de journalisation personnalisée.

```cpp
// USAGE EXAMPLE

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

- [Test unitaire de votre code](../test/unit-test-your-code.md)
- [Écrire des tests unitaires pour C/C++](writing-unit-tests-for-c-cpp.md)
