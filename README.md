flx-gnutls
==========
GnuTLS bindings for felix. Mirrors GnuTLS API for refrence of call behavior refrer to GnuTLS documentaion.
Currently only functionality requred to access TLS sites and establish envrypted session and communication
is implemented which is what I need for not. Pull requests welcome if additional functionality is implemented.
Currently gnutls.fpc is oriented towards Unix man need adjustment for OSX and Windows.

API
---
Type Class: GnuTLS

type gnutls_session_t

type gnutls_anon_client_credentials_t

type gnutls_certificate_credentials_t

type gnutls_transport_ptr_t

type gnutls_credentials_type_t

type gnutls_connection_end_t

type gnutls_close_request_t

type gnutls_x509_crt_fmt_t

const GNUTLS_X509_FMT_PEM:gnutls_x509_crt_fmt_t

const GNUTLS_X509_FMT_DER:gnutls_x509_crt_fmt_t

const GNUTLS_SHUT_RDWR:gnutls_close_request_t

const GNUTLS_SHUT_WR:gnutls_close_request_t

const GNUTLS_CLIENT:gnutls_connection_end_t

const GNUTLS_CRD_ANON:gnutls_credentials_type_t

const GNUTLS_CRD_SRP:gnutls_credentials_type_t

const GNUTLS_CRD_CERTIFICATE:gnutls_credentials_type_t

const GNUTLS_E_SUCCESS:int

fun gnutls_global_init: 1->int 

proc gnutls_deinit: gnutls_session_t 

fun gnutls_check_version: string->string 

fun gnutls_certificate_allocate_credentials: &gnutls_certificate_credentials_t->int 

fun gnutls_handshake: gnutls_session_t->int 

proc gnutls_transport_set_ptr[T in transport_ptr_t]: gnutls_session_t*T 

proc gnutls_perror:int 

fun gnutls_record_recv: gnutls_session_t*address*size->ssize 

fun ssize_to_int:ssize->int 

fun gnutls_strerror:int->string 

fun gnutls_bye:gnutls_session_t * gnutls_close_request_t -> int 

proc gnutls_anon_free_client_credentials:gnutls_anon_client_credentials_t 

proc gnutls_global_deinit:1 

fun gnutls_certificate_set_x509_trust_file: gnutls_certificate_credentials_t * string * gnutls_x509_crt_fmt_t -> int 

fun xgnutls_certificate_set_x509_trust_file: gnutls_certificate_credentials_t * +char * gnutls_x509_crt_fmt_t -> int 

proc gnutls_certificate_free_credentials: gnutls_certificate_credentials_t 

fun alloc_gnutls_certificate_credentials_t: 1->&gnutls_certificate_credentials_t 

proc gnutls_global_set_log_level: int 

proc gnutls_global_set_log_function:1 

fun gnutls_error_is_fatal:int->int 


Example
-------
See httpscat.flx for a usage example. httpscat.fls accepts an ip and a port and issues a GET request and outputs the returned respones to STDOUT.
