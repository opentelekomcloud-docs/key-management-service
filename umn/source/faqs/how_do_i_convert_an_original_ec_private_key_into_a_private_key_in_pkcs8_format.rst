:original_name: dew_01_0472.html

.. _dew_01_0472:

How Do I Convert an Original EC Private Key into a Private Key in PKCS8 Format?
===============================================================================

Scenario
--------

The EC private key is a large integer. However, in the key pair import scenario, the private key must be ASN.1-encoded and then the data must be encoded in binary mode to obtain the DER format, which cannot be obtained by running the OpenSSL command.

This section describes how to convert a 256-bit EC private key into a private key in PKCS8 format.

Environment Preparations
------------------------

-  Create a Java environment and import bouncy castle 1.78 or later.
-  Install OpenSSL 1.1.1m or later.

Converting a Private Key to a PKCS8 Object
------------------------------------------

The following uses a secp256k1 private key as an example. The original private key in hexadecimal format is as follows:

\```DC23DA6E913444ABADCE2F42A3B7DC3958569948633EE80AEC46ACCA02523495``\`

.. note::

   The private key is used as an example only. Do not use it in the actual environment.

Use the following code to convert the private key into a PKCS8 object:

.. code-block::

   ```java
   import org.bouncycastle.jcajce.provider.asymmetric.ec.BCECPrivateKey;
   import org.bouncycastle.jcajce.provider.asymmetric.ec.BCECPublicKey;
   import org.bouncycastle.jce.ECNamedCurveTable;
   import org.bouncycastle.jce.interfaces.ECPrivateKey;
   import org.bouncycastle.jce.provider.BouncyCastleProvider;
   import org.bouncycastle.jce.spec.ECNamedCurveParameterSpec;
   import org.bouncycastle.jce.spec.ECPrivateKeySpec;
   import org.bouncycastle.jce.spec.ECPublicKeySpec;
   import org.bouncycastle.math.ec.ECPoint;

   import java.math.BigInteger;
   import java.security.KeyFactory;
   import java.security.NoSuchAlgorithmException;
   import java.security.PublicKey;
   import java.security.Security;
   import java.security.spec.InvalidKeySpecException;
   import java.security.spec.InvalidParameterSpecException;
   import java.util.Base64;

   public class RawEcPrivateKeyToPKCS8Object {
       public static void main(String[] args)
           throws InvalidParameterSpecException, NoSuchAlgorithmException, InvalidKeySpecException {

           Security.addProvider(new BouncyCastleProvider());

           KeyFactory keyFactory = KeyFactory.getInstance("ECDSA", new BouncyCastleProvider());

           ECNamedCurveParameterSpec ecSpec = ECNamedCurveTable.getParameterSpec("secp256k1");
           BigInteger d = new BigInteger("DC23DA6E913444ABADCE2F42A3B7DC3958569948633EE80AEC46ACCA02523495", 16);
           ECPrivateKeySpec ecPrivateKeySpec = new ECPrivateKeySpec(d, ecSpec);
           BCECPrivateKey ec = new BCECPrivateKey("EC", ecPrivateKeySpec, BouncyCastleProvider.CONFIGURATION);

           ECPoint q = ecSpec.getG().multiply(((ECPrivateKey) ec).getD());
           ECPublicKeySpec pubSpec = new ECPublicKeySpec(q, ecSpec);
           PublicKey publicKey = keyFactory.generatePublic(pubSpec);

           BCECPrivateKey ec2 = new BCECPrivateKey("EC", ec.engineGetKeyParameters(), (BCECPublicKey) publicKey,
               ecPrivateKeySpec.getParams(), BouncyCastleProvider.CONFIGURATION);

           System.out.println(Base64.getEncoder().encodeToString(ec2.getEncoded()));
       }
   }
   ```

The output is as follows:

.. code-block::

   ```ignorelang
   MIGNAgEAMBAGByqGSM49AgEGBSuBBAAKBHYwdAIBAQQg3CPabpE0RKutzi9Co7fcOVhWmUhjPugK7EasygJSNJWgBwYFK4EEAAqhRANCAAQWiYvQT8cyVJx3wN85fXw0c2Ppv3SEsgnDaB96rWlz6G2bf2WhBJVD/jF5zb+5/oxgVIOYDe8EwqYtBwhIJ3Yh
   ```

Use the ASN.1 decoding tool:

.. code-block::

   ```
    <SEQUENCE>
     <INTEGER/>
     <SEQUENCE>
      <OBJECT_IDENTIFIER Comment="ANSI X9.62 public key type" Description="ecPublicKey">1.2.840.10045.2.1</OBJECT_IDENTIFIER>
      <OBJECT_IDENTIFIER Comment="SECG (Certicom) named elliptic curve" Description="secp256k1">1.3.132.0.10</OBJECT_IDENTIFIER>
     </SEQUENCE>
     <OCTET_STRING>
      <SEQUENCE>
       <INTEGER>1</INTEGER>
       <OCTET_STRING>0xDC23DA6E913444ABADCE2F42A3B7DC3958569948633EE80AEC46ACCA02523495</OCTET_STRING>
       <NODE Sign="a0">
        <OBJECT_IDENTIFIER Comment="SECG (Certicom) named elliptic curve" Description="secp256k1">1.3.132.0.10</OBJECT_IDENTIFIER>
       </NODE>
       <NODE Sign="a1">
        <BIT_STRING Bits="520">0x000416898BD04FC732549C77C0DF397D7C347363E9BF7484B209C3681F7AAD6973E86D9B7F65A1049543FE3179CDBFB9FE8C605483980DEF04C2A62D070848277621</BIT_STRING>
       </NODE>
      </SEQUENCE>
     </OCTET_STRING>
    </SEQUENCE>
   ```

Add the following content to the **ec_private_key.pem** file:

.. code-block::

   ```ignorelang
   -----BEGIN PRIVATE KEY-----
   MIGNAgEAMBAGByqGSM49AgEGBSuBBAAKBHYwdAIBAQQg3CPabpE0RKutzi9Co7fcOVhWmUhjPugK7EasygJSNJWgBwYFK4EEAAqhRANCAAQWiYvQT8cyVJx3wN85fXw0c2Ppv3SEsgnDaB96rWlz6G2bf2WhBJVD/jF5zb+5/oxgVIOYDe8EwqYtBwhIJ3Yh
   -----END PRIVATE KEY-----
   ```

Run the following commands to view the EC key information:

.. code-block::

   ```shell
   openssl ec -in ec_private_key.pem -text
   ```
   ```ignorelang
   read EC key
   Private-Key: (256 bit)
   priv:
       dc:23:da:6e:91:34:44:ab:ad:ce:2f:42:a3:b7:dc:
       39:58:56:99:48:63:3e:e8:0a:ec:46:ac:ca:02:52:
       34:95
   pub:
       04:16:89:8b:d0:4f:c7:32:54:9c:77:c0:df:39:7d:
       7c:34:73:63:e9:bf:74:84:b2:09:c3:68:1f:7a:ad:
       69:73:e8:6d:9b:7f:65:a1:04:95:43:fe:31:79:cd:
       bf:b9:fe:8c:60:54:83:98:0d:ef:04:c2:a6:2d:07:
       08:48:27:76:21
   ASN1 OID: secp256k1
   writing EC key
   -----BEGIN EC PRIVATE KEY-----
   MHQCAQEEINwj2m6RNESrrc4vQqO33DlYVplIYz7oCuxGrMoCUjSVoAcGBSuBBAAK
   oUQDQgAEFomL0E/HMlScd8DfOX18NHNj6b90hLIJw2gfeq1pc+htm39loQSVQ/4x
   ec2/uf6MYFSDmA3vBMKmLQcISCd2IQ==
   -----END EC PRIVATE KEY-----

   ```

If the commands can be executed properly, the following **DER** command is generated:

.. code-block::

   ```shell
   openssl pkcs8 -topk8 -inform PEM -outform DER -in ec_private_key.pem -out ec_private_key.der -nocrypt```
