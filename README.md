1. What are the key differences between unary, server streaming, and bi-directional streaming RPC (Remote Procedure Call) methods, and in what scenarios would each be most suitable?
> In unary RPC, the client sends a single request and recieves a single response, whilst in server and bi-directional streaming the client can send a single request and a stream respectively and recieve a stream of responses. Unary RPC is best applied in CRUD operations, stream RPC is best in pagination or file downloads, and bi-directional streaming is best in chatting or real time applications.

2. What are the potential security considerations involved in implementing a gRPC service in Rust, particularly regarding authentication, authorization, and data encryption?
> Every individual message in the stream would have to be individually authenticated and encrypted.
3. What are the potential challenges or issues that may arise when handling bidirectional streaming in Rust gRPC, especially in scenarios like chat applications?
> Handling multiple concurrent streams would require careful design of asynchronous task coordination.
4. What are the advantages and disadvantages of using the tokio_stream::wrappers::ReceiverStream for streaming responses in Rust gRPC services?
> Advantages: Works naturally with async/await syntax, built in backpressure management. Disadvantages: Slight performance overhead, requires wrapping each message in Result types, overall harder to design effectively.
5. In what ways could the Rust gRPC code be structured to facilitate code reuse and modularity, promoting maintainability and extensibility over time?
> Separate service definitions from implementations, organize code by business domains (rather than technical layers), separate core business logic from external interfaces.
6. In the MyPaymentService implementation, what additional steps might be necessary to handle more complex payment processing logic?
> Input validation, fraud detection, circuit breakers, idempotency handling, transaction states.
7. What impact does the adoption of gRPC as a communication protocol have on the overall architecture and design of distributed systems, particularly in terms of interoperability with other technologies and platforms?
> Proto files become the source of truth/contract between services, encourages explicit service interfaces with well defined RPCs, enables unary, streaming bidirectional RPCs
8. What are the advantages and disadvantages of using HTTP/2, the underlying protocol for gRPC, compared to HTTP/1.1 or HTTP/1.1 with WebSocket for REST APIs?
> HTTP/2 allows multiplexing, more efficient binary protocol, header compresssion, and beter connection efficiency.
9. How does the request-response model of REST APIs contrast with the bidirectional streaming capabilities of gRPC in terms of real-time communication and responsiveness?
> In the REST request response model, it's connectionless, unidirectional, and stateless. but GRPC Bidirectional streaming is connection based, stteful stream and push based.Overall GRPC is faster and more responsive.
11. What are the implications of the schema-based approach of gRPC, using Protocol Buffers, compared to the more flexible, schema-less nature of JSON in REST API payloads?
> Protobuf forces strong type checking, contract enforcement, while JSON has runtime type validation and loose contracts. 