**Hibernate object state**

Hibernate object state can be

* transient: just created POJO
* persistent: currently associcated with live session
* detached w.r.t a session: associated with an other session, that may be live or closed

Transient becomes persistent by `session.save`. Detached become transient by `session.update`.

* http://docs.jboss.org/hibernate/core/3.3/reference/en/html/objectstate.html#objectstate-makingpersistent
