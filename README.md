NSAC ENGINEERING TEST

Time allowed: 1 hour 30 minutes
Total marks: 100

---

Instructions
You may use official documentation for programming languages, libraries, APIs and other software tools. You must work independently. Generative AI and AI-assisted programming tools are not permitted.

You may use any programming language unless a question specifies otherwise. You are not expected to have prior knowledge of NASA, remote sensing, geographic information systems or any particular scientific dataset. Any information required to answer a question will be given. Your code should be sufficiently clear that another programmer can understand and run it. 

Additional Instructions 
Where a question asks for a program, write working code. Where a question asks for an explanation, give a clear reason. Show your working where a calculation or conclusion depends on it. State any assumptions you make. If a question cannot be completed because information is missing, identify what is missing and explain how it affects your answer.

---

1 Observations

A field unit records environmental observations.

The following records are received:

ID| Type| Value| Time| Latitude| Longitude| Source
101| temperature| 31.4 °C| 14:00| 25.4210| 89.5010| S1
102| temperature| 31.9 °C| 14:05| 25.4210| 89.5010| S1
103| water_level| 2.41 m| 14:01| 25.4210| 89.5010| S1
104| fire| 0.91| 14:03| 25.4210| 89.5010| S2
105| rainfall_probability| 82 %| 13:00| 25.4210| 89.5010| S3
106| surface_fraction| 0.63| 09:20| 25.4210| 89.5010| S4
107| temperature| —| 14:06| 25.4210| 89.5010| S1
108| temperature| 91.7 °C| 14:07| 25.4210| 89.5010| S1

The documentation for S2 states:

«The value recorded for "fire" is the confidence assigned by an image-classification model. It is not a direct measurement of fire.»

The documentation for S4 states:
«"surface_fraction" is an estimated fraction of the observed area occupied by the specified surface class. Values range from 0 to 1.»

(a)

Identify two records which require special handling before they are used.
For each record, state the reason.

[4]

(b)

The value in record 107 is missing.
A programmer proposes replacing it with zero.
Explain why this may change the meaning of the observation.

[2]

(c)

The value in record 108 is unusually large.
Give two reasons why it should not simply be deleted without investigation.

[2]

(d)

Write a suitable representation for an observation which can contain:

- its type;
- value;
- time;
- location;
- source;
- confidence or uncertainty where applicable.

The same representation should be usable for different types of observation.

[4]

[Total: 12]

---

2 Position

The field unit reports its position as:

latitude:  25.4200
longitude: 89.5000

The following observations are available:

Observation| Latitude| Longitude
P| 25.4210| 89.5010
Q| 25.4300| 89.5000
R| 25.9000| 89.7000
S| 25.4200| 89.6000
T| 91.0000| 89.5000

(a)

Identify the invalid coordinate.

[1]

(b)

Write a function which accepts two valid geographic coordinates and returns their approximate distance in metres.

[5]

(c)

Explain why
sqrt((lat1 - lat2)^2 + (lon1 - lon2)^2)

does not generally represent the distance between two points on Earth.

[2]

(d)

The user requests all observations within 500 m of their current position.
Write code which returns the appropriate observations.

[4]

[Total: 12]

---

3 A measurement is not a conclusion

The camera produces the following classifications:

Image| Classification| Confidence
1| water| 0.82
2| water| 0.77
3| road| 0.61
4| water| 0.54

The model documentation states:
«A confidence value describes the model's confidence in its classification. It does not represent the probability that the classification is physically correct.»

(a)

Which image has the greatest model confidence for the classification "water"?

[1]

(b)

A user states:
«“There is an 82% probability that water is present.”»

Explain why this statement is not established by the information given.

[3]

(c)

The model was trained using images taken during daylight. Image 4 was taken at night.
Explain why this may affect the interpretation of its result.

[2]

(d)

State two pieces of information which could be stored with a classification to help a later user assess it.

[2]

[Total: 8]

---

4 Comparing observations

Four sources provide information about the same area.

Source| Observation| Time| Spatial coverage
Local sensor| water level = 2.41 m| 14:01| one point
Camera| water confidence = 0.82| 14:03| image
Satellite| surface fraction = 0.63| 09:20| 2 km × 2 km
Weather service| rainfall probability = 82 %| 13:00| regional

(a)

Give one reason why these four values should not simply be averaged.

[2]

(b)

Give one important difference between the information supplied by the local sensor and the satellite observation.

[2]

(c)

Write three statements which can be made from the information in the table without adding information that is not given.

[3]

(d)

Write one statement which cannot be justified from the table.
Explain why.

[2]

[Total: 9]

---

5 Change over time

Measurements from one location are recorded as follows:

Date| Measurement
1 January| 10.2
8 January| 10.5
15 January| 10.4
22 January| 10.6
29 January| 16.8

The system uses the following rule:
«Report a change when the latest valid measurement differs from the earliest valid measurement by at least 40%.»

(a)

Determine whether the observations satisfy the rule.
Show your calculation.

[3]

(b)

Write a function which implements the rule.
The threshold must be supplied to the function.

[4]

(c)

Consider the observations:

10, 10, 10, 15

Explain why the percentage change obtained using the first observation as the reference differs from the percentage change obtained using the mean of the preceding observations as the reference.

[2]

[Total: 9]

---

6 Earth-observation data

A satellite product provides the following information.
«"surface_fraction" is an estimated fraction of the observation area occupied by a particular surface class.
"quality_flag = 0" indicates that the observation is invalid.
Observations produced using different processing versions must not be combined unless the documentation explicitly permits this.»

Location| Date| Surface fraction| Quality flag| Version
A| 1 May| 0.42| 1| v3
A| 1 June| 0.51| 1| v3
A| 1 July| 0.49| 0| v3
A| 1 August| 0.62| 1| v4
B| 1 May| 0.18| 1| v3
B| 1 June| 0.22| 1| v3

(a)

Which observations for location A may be compared without further information?

[2]

(b)

A report states:
«“The surface fraction at A increased from 0.42 to 0.62.”»

Explain why the available information does not establish this comparison.

[3]

(c)

Write a function which receives observations in this format and returns only comparisons permitted by the rules above.
The function must also work for other locations and dates.

[6]

[Total: 11]

---

7 External information

The field unit obtains additional observations from an external service.
A successful response has the following form:

{
    "page": 1,
    "pages": 2,
    "observations": [
        {
            "id": "1842",
            "location_id": "A",
            "status": "valid",
            "value": 42.7
        }
    ]
}

The service may return:

- an HTTP error;
- an empty observation list;
- an observation with a missing value;
- an unknown "location_id";
- a response with status code 200 but without the "observations" field.

(a)

Write a function which retrieves all available pages.
The function must not assume that the number of pages is always two.

[5]

(b)

The server returns status code 200 but no "observations" field.
State how the program should handle this response and give a reason.

[2]

(c)

The server returns an observation whose "location_id" does not exist in the local dataset.
State how the program should handle it.

[2]

(d)

Write one automated test for the function.

[2]

[Total: 11]

---

8 When the connection is lost

At 15:00 the network connection becomes unavailable.
The device still contains:

- a temperature measurement taken at 14:55;
- a camera image taken at 14:58;
- satellite data downloaded at 09:20;
- weather information downloaded at 13:00;
- the user's current position.

(a)

State two types of information which the device can continue to provide without a network connection.

[2]

(b)

State two types of information which the device should not present as current if they require a successful connection to the external service.

[2]

(c)

Explain why the time at which information was observed should be stored separately from the time at which it was downloaded.

[2]

(d)

Suggest a way of storing cached information so that the system can distinguish between recent and old information.

[3]

[Total: 9]

---

9 Limited resources

The device has:

RAM available: 2 GB
Free storage: 500 MB
Network: unavailable

A satellite image occupies 1.8 GB.

The user requires information about an area occupying approximately 5% of the image.
Two approaches are proposed.

Approach A
Load the entire image into memory whenever information is requested.

Approach B
Prepare or store a smaller representation and process only the required area where possible.

(a)

Which approach is more suitable under the stated conditions?

[1]

(b)

Give two reasons for your answer.

[2]

(c)

Give one disadvantage of the approach you selected.

[2]

(d)

Suggest one method by which useful information could be retained while reducing the amount of storage required.

[2]

[Total: 7]

---

10 Software design

The system currently accepts observations of the following types:

temperature
water_level
rainfall
surface_fraction

It may later receive:

vegetation
fire
air_quality
soil_moisture
terrain
wind

A programmer has written a separate top-level processing system for every observation type.

(a)

State one disadvantage of this design.

[2]

(b)

Propose a common representation which could be used for the different observation types.

[3]

(c)

Write a small example showing how a new observation type could be added using your representation.

[4]

[Total: 9]

---

11 Finding an error

The following function is used to calculate percentage change.

def change(first, last):
    return (last - first) / first * 100

For:

first = 10
last = 12.5

the program displays:

0.25

(a)

State the error.

[1]

(b)

Give the correct result.

[1]

(c)

Write an automated test which would detect the error.

[3]

(d)

The function is called with:

first = 0

Explain why the existing function is insufficient.

[2]

(e)

Modify the function so that this case is handled explicitly.

[3]

[Total: 10]

---

12 Change of specification

The original reporting rule is:
«Report a change when the latest valid observation differs from the earliest valid observation by at least the supplied threshold.»

The requirement is changed to:
«A change may only be reported when at least three valid observations are available. The latest observation must differ from the mean of all preceding valid observations by at least the supplied threshold.»

Consider:

10, 12, 11, 20

(a)

Calculate the reference value for the final observation.

[2]

(b)

Determine whether the final observation differs from the reference value by at least 50%.

[2]

(c)

Modify your existing implementation to use the new rule.

[5]

(d)

State one test which should be added or changed as a result of the new requirement.

[1]

[Total: 10]

---

13 Final report

The system has established the following:

- three valid observations were obtained;
- all three used the same measurement procedure;
- the latest measurement is approximately 17.4% higher than the earliest;
- a camera classification was also obtained;
- the cause of the measured change is unknown;
- no prediction has been produced.

A report contains:

{
    "location": "A",
    "change": 17.4,
    "confidence": 0.71,
    "hazard": "flood"
}

(a)

Identify one field in the report whose meaning is not adequately supported by the information available.

[1]

(b)

Suggest how the report could represent the available evidence more accurately.

[3]

(c)

State one additional piece of information which could allow a stronger conclusion to be made.

[1]

[Total: 5]

---

Submission

Submit the following:

README.md
src/
data/
tests/
output/

Your submission must contain:

- the working implementation;
- machine-readable output;
- at least three automated tests;
- handling of invalid or incomplete observations;
- handling of external information;
- the revised requirement from Question 12;
- important assumptions and limitations.

Disclaimer: This is a quite simple test 

---

End of Paper
