# Geoproximity

Geoproximity routing lets R53 route traffic to your resources based on the geographic location of your users and your resources. You can also optionally choose to route more traffic or less to a given resource by specifying a value, known as a bias. A bias expands or shrinks the size of the geographic region from which traffic is routed to a resource.

As an example, say you have resources in the U.K. and in Australia. Now, you want to route users from Saudi Arabia to your Australia resources instead of your U.K. based ones. Normally, with a pure distance based approach, they would be routed to the U.K. based resources. However, if you specify a bias, you can expand the size of the geographic region that would be routed to a particular resource and can ensure that those users are routed to the Australia resource still.

